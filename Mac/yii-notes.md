## Yii 开发笔记

### 创建user数据表迁移

> 在我们开发程序的过程中，数据库的结构也是不断调整的。我们的开发中要保证代码和数据库库的同步。因为我们的应用离不开数据库。例如: 在开发过程中，我们经常需要增加一个新的表，或者我们后期投入运营的产品，可能需要为某一列添加索引。我们必须保持数据结构和代码的一致性。如果代码和数据库不同步，可能整个系统将无法正常运行。出于这个原因。yii提供了一个数据库迁移工具，可以保持代码和数据库是同步。方便数据库的回滚和更新。

#### 配置

修改config/console.php，加入migrate配置:

    return array(
        'basePath'=>...

        ...

        'commandMap' => array(
            // Database migration
            'migrate' => array(
                'class'=>'system.cli.commands.MigrateCommand',
                'migrationPath'=>'application.migrations',
                'migrationTable'=>'tbl_migration',
                'connectionID'=>'db',
                'templateFile'=>'application.migrations.template',
            ),
        ),
    );

#### 创建迁移
    
目前还没有任何数据表，运行以下命令创建数据库迁移

	php yiic.php migrate create create_user_table

![image](https://app.yinxiang.com/shard/s2/res/a3d4cab9-02d1-4c21-9741-a00b15422d4e.jpg?resizeSmall&width=1100)
