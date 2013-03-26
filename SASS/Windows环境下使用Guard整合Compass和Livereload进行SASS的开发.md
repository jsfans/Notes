## Windows环境下使用Guard整合Compass和Livereload进行SASS的开发

### 配置运行环境

Guard，Compass 和 Livereload 是 Ruby 的 Gem 套件，需要 Ruby 运行环境。另外还需要安装 Ruby 的扩展开发包 Development-Kit，以实现 Livereload 的功能和 SASS 的编译。最后需要 Bundler 用于打包 Gem 依赖。

+ **安装 Ruby**  
  - 下载并安装 [Rubyinstaller][Rubyinstaller Download link]。
  - 安装过程中勾选相关设置，这样可以直接通过cmd命令行操作（不必手动添加Path）。
  - 安装完成后，在 CMD 窗口运行 `ruby --version`，若安装成功会显示 Ruby 版本信息。

+ **安装 Development-Kit**  
  - 下载 [Development-Kit][Development-Kit Download link]。
  - 将其解压到某个目录，例如：C:/DevKit/。
  - 打开你的Development-Kit所在的位置，在里面执行以下命令：

```ruby
ruby dk.rb init
ruby dk.rb install
```

+ **安装 Bundler**
  - 更新 Gem 系统，然后安装 Bundler：

```cmd
gem update --system
gem install bundler
```

### 运行 Guard



### 给浏览器安装 Livereload 插件

[Rubyinstaller Download link]: http://rubyinstaller.org/downloads/
[Development-Kit Download link]: http://rubyinstaller.org/downloads/