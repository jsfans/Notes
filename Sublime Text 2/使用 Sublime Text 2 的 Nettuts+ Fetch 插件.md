## 使用 Sublime Text 2 的 Nettuts+ Fetch 插件

做项目的时候你或许需要使用最新版本的jQuery，又或者是类似HTML5 Boilerplate这样的开发包，目前你的做法可能是：访问官网，导航到下载地址；或许直接有困难找百度。

有没有一种简单方法可以很轻松地获取某些文件或开发包的最新版呢？

Sublime Text 2 及其 Nettuts+ Fetch 插件粉墨登场。

### 安装 Nettuts+ Fetch 插件

Nettus+ Fetch 安装方法很简单：

* 最简单是通过 [Package Control][Package Control] 安装
* 也可以手动下载 [Nettuts+ Fetch 的安装包][Nettuts+ Fetch]

### 使用方法

*   管理配置列表：通过命令框（`Cmd+Shift+P`，Windows系统：`Ctrl+Shift+P`）键入`Fetch: Manage`，接着会打开配置文件让你编辑。

    例如加入jQuery的文件和HTML5 Boilerplate开发包可以这样写：

		{
			"files":
			{
				"jquery": "http://code.jquery.com/jquery.min.js"
			},
			"packages":
			{
				"html5-boilerplate": "https://github.com/h5bp/html5-boilerplate/zipball/master"
			}
		}

    本文最后会附上一些“常用的”文件和包的配置，可以按自己的需要引用。

*   Fetch 最新的文件：通过命令框键入`Fetch: File`，在下拉列表（上述配置文件中定义）中选择目标文件回车。

*   Fetch 最新的包：通过命令框键入`Fetch: Package`，在下拉列表中选择目标包回车。

### 一些文件和包的配置

	{
		"files":
		{
			"Dynamic-Carousel": "https://raw.github.com/Wilto/Dynamic-Carousel/master/plugin.js",
			"FitText": "https://raw.github.com/davatron5000/FitText.js/master/jquery.fittext.js",
			"FitVids": "https://raw.github.com/davatron5000/FitVids.js/master/jquery.fitvids.js",
			"backbone": "http://documentcloud.github.com/backbone/backbone.js",
			"backbone.min": "http://documentcloud.github.com/backbone/backbone-min.js",
			"history": "https://raw.github.com/balupton/history.js/master/scripts/compressed/history.js",
			"jquery": "http://code.jquery.com/jquery.js",
			"jquery-cookie": "https://raw.github.com/carhartl/jquery-cookie/master/jquery.cookie.js",
			"jquery-dotimeout": "https://raw.github.com/cowboy/jquery-dotimeout/master/jquery.ba-dotimeout.min.js",
			"jquery-extra-selectors": "https://raw.github.com/keithclark/JQuery-Extended-Selectors/master/jquery-extra-selectors.js",
			"jquery-flexslider": "https://raw.github.com/mbmufffin/FlexSlider/master/jquery.flexslider-min.js",
			"jquery-mediaelement": "https://raw.github.com/johndyer/mediaelement/master/build/mediaelement-and-player.js",
			"jquery-min": "http://code.jquery.com/jquery.min.js",
			"jquery-mobile": "http://code.jquery.com/mobile/1.0.1/jquery.mobile-1.0.1.min.js",
			"jquery-mobile-vmouse": "https://raw.github.com/jquery/jquery-mobile/master/js/jquery.mobile.vmouse.js",
			"jquery-mousewheel": "https://raw.github.com/brandonaaron/jquery-mousewheel/master/jquery.mousewheel.js",
			"jquery-ui-effects": "https://raw.github.com/jquery/jquery-ui/master/ui/jquery.effects.core.js",
			"jquery-url": "https://raw.github.com/allmarkedup/jQuery-URL-Parser/master/jquery.url.js",
			"jquery.min": "http://code.jquery.com/jquery.min.js",
			"json2": "https://raw.github.com/douglascrockford/JSON-js/master/json2.js",
			"knockout": "https://raw.github.com/SteveSanderson/knockout/master/build/output/knockout-latest.js",
			"modernizr": "https://raw.github.com/Modernizr/Modernizr/master/modernizr.js",
			"normalize": "https://raw.github.com/necolas/normalize.css/master/normalize.css",
			"performermin": "http://performerjs.org/download/performer-min.js",
			"prefixfree": "https://raw.github.com/LeaVerou/prefixfree/master/prefixfree.min.js",
			"reset": "http://meyerweb.com/eric/tools/css/reset/reset.css",
			"respond": "https://raw.github.com/keithclark/Respond/master/respond.min.js",
			"selectivizr": "https://raw.github.com/keithclark/selectivizr/master/selectivizr.js",
			"twitter-bootstrap-alerts": "https://raw.github.com/twitter/bootstrap/master/js/bootstrap-alerts.js",
			"twitter-bootstrap-buttons": "https://raw.github.com/twitter/bootstrap/master/js/bootstrap-buttons.js",
			"twitter-bootstrap-carousel": "https://raw.github.com/twitter/bootstrap/master/js/bootstrap-carousel.js",
			"twitter-bootstrap-collapse": "https://raw.github.com/twitter/bootstrap/master/js/bootstrap-collapse.js",
			"twitter-bootstrap-dropdown": "https://raw.github.com/twitter/bootstrap/master/js/bootstrap-dropdown.js",
			"twitter-bootstrap-modal": "https://raw.github.com/twitter/bootstrap/master/js/bootstrap-modal.js",
			"twitter-bootstrap-popover": "https://raw.github.com/twitter/bootstrap/master/js/bootstrap-popover.js",
			"twitter-bootstrap-scrollspy": "https://raw.github.com/twitter/bootstrap/master/js/bootstrap-scrollspy.js",
			"twitter-bootstrap-tabs": "https://raw.github.com/twitter/bootstrap/master/js/bootstrap-tabs.js",
			"twitter-bootstrap-tooltip": "https://raw.github.com/twitter/bootstrap/master/js/bootstrap-tooltip.js",
			"twitter-bootstrap-transition": "https://raw.github.com/twitter/bootstrap/master/js/bootstrap-transition.js",
			"twitter-bootstrap-twipsy": "https://raw.github.com/twitter/bootstrap/master/js/bootstrap-twipsy.js",
			"twitter-bootstrap-typehead": "https://raw.github.com/twitter/bootstrap/master/js/bootstrap-typehead.js",
			"underscore": "http://documentcloud.github.com/underscore/underscore.js",
			"underscore.min": "http://documentcloud.github.com/underscore/underscore-min.js"
		},
		"packages":
		{
			"320 and up": "https://github.com/malarkey/320andup/zipball/master",
			"Backbone Boilerplate": "https://github.com/tbranyen/backbone-boilerplate/zipball/master",
			"Foundation by Zurb": "https://github.com/zurb/foundation/zipball/master",
			"Grunt": "https://github.com/cowboy/grunt/zipball/master",
			"Impress.js": "https://github.com/bartaz/impress.js/zipball/master",
			"Twitter Bootstrap": "https://github.com/twitter/bootstrap/zipball/master",
			"WordPress": "http://wordpress.org/latest.zip",
			"Yii": "https://github.com/yiisoft/yii/zipball/master",
			"Zend Framework": "https://github.com/zendframework/zf2/zipball/master",
			"blankwork": "http://www.blankwork.net/blankwork-latest.zip",
			"codeigniter": "http://codeigniter.com/download.php",
			"ember": "https://github.com/emberjs/ember.js/zipball/master",
			"handelbars": "https://github.com/wycats/handlebars.js/zipball/master",
			"html5-boilerplate": "https://github.com/h5bp/html5-boilerplate/zipball/master",
			"html5-boilerplate-stripped": "https://github.com/h5bp/html5-boilerplate/zipball/v3.0stripped",
			"html5-reset": "https://github.com/murtaugh/HTML5-Reset/zipball/master",
			"mobile-boilerplate": "https://github.com/h5bp/mobile-boilerplate/zipball/v3.0",
			"mobile-boilerplate-stripped": "https://github.com/h5bp/mobile-boilerplate/zipball/v3.0stripped",
			"skeleton": "https://nodeload.github.com/dhgamache/Skeleton/zipball/master"
		}
	}

[Package Control]: http://wbond.net/sublime_packages/package_control 
[Nettuts+ Fetch]: https://github.com/weslly/Nettuts-Fetch

