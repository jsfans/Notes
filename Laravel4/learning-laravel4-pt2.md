## Laravel 4 笔记整理2 - 数据库迁移和播种

### 配置数据库

以默认的数据库配置文件作为蓝本并修改连接信息：

	cp app/config/database.php app/config/local
	vi app/config/local/database.php

如果使用 mysql 数据库，那么修改后的数据库连接信息应该像下面这样：

    'connections' => array(
        'mysql' => array(
            'driver'    => 'mysql',
            'host'      => 'localhost',
            'database'  => 'read_it_later',
            'username'  => 'your_username',
            'password'  => 'your_password',
            'charset'   => 'utf8',
            'collation' => 'utf8_unicode_ci',
            'prefix'    => '',
        ),
    ),

### 运行 Sentry 的迁移

我们使用 Sentry 进行用户验证，而 Sentry 已经自带了数据库迁移，我们所要做的仅仅是运行这些迁移：

	php artisan migrate --package=cartalyst/sentry

刷新数据库，应该可以看到 Sentry 创建了 users，groups，users_groups，throttle 这四个表。

### 创建文章和页面的迁移

[Laravel-4-Generators][Laravel-4-Generators in github] 已经在前面安装好了，我们使用它来轻松创建迁移：

	php artisan generate:migration create_posts_table --fields="title:string, slug:string, body:text:nullable, image:string:nullable, user_id:integer"

	php artisan generate:migration create_pages_table --fields="title:string, slug:string, body:text:nullable, user_id:integer"

运行迁移：

	php artisan migrate

刷新数据库，可以看到 posts 和 pages 这两个数据表已经为我们创建好了。

### 模型

**创建模型：**

    php artisan generate:model post

    php artisan generate:model page

在目录 `app/models/` 中可以看到生成的 `Post.php` 和 `Page.php` ，文件填充了一些基本的骨架代码，现在修改它们：

**app/models/Post.php**

```php
<?php

class Post extends Eloquent {

    protected $table = 'posts';

    protected $guarded = array();

    public static $rules = array();

    public function author()
    {
        return $this->belongsTo('User');
    }
}
```

**app/models/Page.php**

    <?php

    class Page extends Eloquent {

        protected $table = 'pages';

        protected $guarded = array();

        public static $rules = array();

        public function author()
        {
            return $this->belongsTo('User');
        }
    }


### 创建播种器

还是请出强大的 [Laravel-4-Generators][Laravel-4-Generators in github] ：


[Laravel-4-Generators in github]: https://github.com/JeffreyWay/Laravel-4-Generators
