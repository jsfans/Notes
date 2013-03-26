# Windows环境下使用Guard整合Compass和Livereload进行SASS的开发
------

## 配置运行环境

Guard，Compass 和 Livereload 是 Ruby 的 Gem 套件，需要 Ruby 运行环境。另外还需要安装 Ruby 的扩展开发包 Development-Kit，以实现 Livereload 的功能和 SASS 的编译。最后需要 Bundler 用于打包 Gem 依赖。

### 安装 Ruby
  - 下载并安装 [Rubyinstaller](http://rubyinstaller.org/downloads/)。
  - 安装过程中勾选相关设置，这样可以直接通过cmd命令行操作（不必手动添加Path）。
  - 安装完成后，在 CMD 窗口运行 `ruby --version`，若安装成功会显示 Ruby 版本信息。

### 安装 Development-Kit  
  - 下载 [Development-Kit](http://rubyinstaller.org/downloads/)。
  - 将其解压到某个目录，例如：C:/DevKit/。
  - 打开你的Development-Kit所在的位置，在里面执行以下命令：

```ruby
ruby dk.rb init
ruby dk.rb install
```

### 安装 Bundler
  - 更新 Gem 系统，然后安装 Bundler：

```cmd
gem update --system
gem install bundler
```

### 使用 Bundler 打包所需的 gem 依赖

+ 打开用户目录，增加 Gemfile 和 .Guardfile 这两个文件（文件内容见文末附件）。
+ Shift+右键调出当前目录CMD窗口，运行如下命令：

	```cmd
	bundle
	```

Bundler 会根据 Gemfile 中的配置安装 Compass 和 SASS 等 gem，安装过程会比较久，打杯水静静等待 gem 安装完成或执行下一步安装浏览器的 Livereload 插件。

## 给浏览器安装 Livereload 插件

**Safari**：[Safari extension 2.0.9](http://download.livereload.com/2.0.9/LiveReload-2.0.9.safariextz)

**Chrome**：[Chrome extension on the Chrome Web Store](https://chrome.google.com/webstore/detail/livereload/jnihajbhpnppcggbcgedagnkighmdlei)

**Firefox**：[Firefox extension 2.0.8](http://download.livereload.com/2.0.8/LiveReload-2.0.8.xpi)

详见 Livereload 的官网：[http://feedback.livereload.com/knowledgebase/articles/86242-how-do-i-install-and-use-the-browser-extensions-](http://feedback.livereload.com/knowledgebase/articles/86242-how-do-i-install-and-use-the-browser-extensions-)

## 运行 Guard

+ 在项目目录中运行：`guard`。
+ 打开浏览器，点击浏览器的 Livereload 图标。

至此完成所有的配置，Compass 会检测 Gemfile 定义文件的改动，生成 CSS，并自动刷新浏览器。

## 附件

以下是 Gemfile 和 .Guardfile 的内容：

**Gemfile**

```ruby
source "http://rubygems.org"

group :development do
  gem 'compass' # Depends on Sass, will be installed automatically.
  # gem 'compass-960-plugin' # 960.gs
  # gem 'compass-validator' # So you can `compass validate`.
  # gem 'oily_png' # Faster Compass sprite generation.
  # gem 'css_parser' # Helps `compass stats` output statistics.
  gem 'guard-compass' # Compile on sass/scss change.
  gem 'guard-livereload' # Browser reload.
  gem 'yajl-ruby' # Faster JSON with LiveReload in the browser.
end
```

**.Guardfile**

```ruby
# More info at https://github.com/guard/guard#readme

notification :off

# Current watch directory must contain the Compass config file.
if File.exists?("./config.rb")
  # https://github.com/guard/guard-compass
  guard 'compass' do
    watch(%r{(.*)\.s[ac]ss$})
  end
end

# If current or child directories has files we want to monitor for live changes.
# This may throw an error with ruby < 1.9.
require 'find'
if Find.find(Dir.pwd).detect{|dir|dir=~/.+\.(css|js|html?|php|inc)$/}
  # https://github.com/guard/guard-livereload
  guard 'livereload' do
    watch(%r{.+\.(css|js|html?|php|inc)$})
  end
end
```




