Date: 2013-07-29  
Title: Sublime-text 2 的配置   
Published: true  
Type: post  
Slug: sublime-text-2-settings  
Tags: sublime-text

### Package Control

1. Control + ` 调出 Sublime 的命令行；
2. 将以下代码粘贴进命令行中并回车：
	
		import urllib2,os;pf='Package Control.sublime-package';ipp=sublime.installed_packages_path();os.makedirs(ipp) if not os.path.exists(ipp) else None;open(os.path.join(ipp,pf),'wb').write(urllib2.urlopen('http://sublime.wbond.net/'+pf.replace(' ','%20')).read())
	
3. 重启 Sublime Text 2，如果在 Preferences -> Package Settings中见到Package Control这一项，就说明安装成功了。

### 代码片段

1. 使用 Package Control 安装 Emmet 插件；
2. 添加如下配置信息，禁用 Emmet 的 CSS Snippet 功能：

    	{
			"disable_tab_abbreviations_for_scopes": "source.css, source.scss"
    	}
   
### Javascript 语法检测

1. 命令行安装 node：

		brew install node

2. 使用 npm 安装 jshint：

		npm install -g jshint

3. 使用 Package Control 安装 JsHint 插件；

4. 使用 Package Control 安装 SublimeOnSaveBuild 插件，让其可以在 js 文件保存时自动检测。

### Markdown 的使用

1. **修改保存 Markdown 文件的后缀为 .md**
	新建 Markdown.sublime-settings 保存以下内容，并丢入 Packages/User/
	
		{
			"extensions": ["md"]
		}

2. **设置新建文件默认为 Markdown 格式**
   - 使用 Package Control 安装 Default File Type;
   - 新建 default_file_type.sublime-settings 保存以下内容，并丢入 Packages/User/

			{
				"default_new_file_syntax":"Packages/Markdown/Markdown.tmLanguage",
				"use_current_file_syntax":true
			}
	
3. **自定义 Markdown 高亮配色方案**
   - 默认 Packages/Color Scheme - Default/Monokai.thTheme 配色里是没有MD高亮的，所以网上搜来份并微调之，点击下载： Monokai-custom.tmTheme ；
   - 为避免之后主程序升级覆盖，把下载到的文件丢入 Packages/User/ ；
   - 打开 Packages/User/Preferences.sublime-settings 加入以下这条
	
			{
				"color_scheme": "Packages/User/Monokai-custom.tmTheme"
			}

4. **一键导出 HTML 代码**；
   - 使用 Package Control 安装 Markdown2Clipboard ；
   - 在 MD 文件中直接鼠标右键 Copy Markdown as HTML ;
	
5. **Markdown相关插件**
   - Markdown Preview - 预览 Markdown
   - SmartMardown - 智能的 Markdown 书写

### 其他插件和配置 

- JsFormat：Javascript 格式化
- Tag：HTML 格式化
- ClipBoard History：使用剪贴板记录
- Gist：使用 Github 提供的代码片段存储服务。
- SCSS：让 Sublime 支持 SCSS 语法
- Nettuts+ Fetch：方便常用库文件更新
- SideBarEnhancements：侧栏右键增强插件
- Soda：皮肤插件
- Centurion：皮肤插件

附配置一份：

    {
        // Colors
        "color_scheme": "Packages/Color Scheme - Default/Sunburst.tmTheme",
        "theme": "Centurion.sublime-theme",

        // Font
        "font_face": "Ubuntu Mono",
        "font_size": 18.0,
        "font_options": ["subpixel_antialias", "no_bold"],
        "line_padding_bottom": 0,
        "line_padding_top": 0,

        // Cursor style - no blinking and slightly wider than default
        "caret_style": "solid",
        "wide_caret": true,

        // Editor view look-and-feel
        "highlight_line": true,
        "word_wrap": true,

        // Whitespace - no tabs, trimming, end files with \n
        "tab_size": 4,
        "translate_tabs_to_spaces": true,
        "trim_trailing_white_space_on_save": true,
        "ensure_newline_at_eof_on_save": true,

        // Vintage
        "ignored_packages":
        [
        ],
        "vintage_ctrl_keys": true,
        "vintage_start_in_command_mode": true,

        // Sidebar - exclude distracting files and folders
        "file_exclude_patterns":
        [
            ".DS_Store"
        ],
        "folder_exclude_patterns":
        [
            ".git",
            ".svn",
            ".sass-cache"
        ]

    }




 

