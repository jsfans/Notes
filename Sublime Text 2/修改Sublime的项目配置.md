## 修改Sublime的项目配置

打开项目配置文件：XXX.sublime-project，可作如下修改：

    {
         "folders": // 可添加多个目录：{...},{...}
         [
              {
                   "path": "/E/webroot/backbone-learning", // 项目目录
                   "folder_exclude_patterns": ["assets",".sass-cache"] // 排除目录
              }
         ],
        "settings":
        {
            "translate_tabs_to_spaces": true, // Tab是否转换成空格
            "tab_size": 4
        }
    }

在每个项目的文件数组配置中，可以设置不同的内容:

1. `path` (string): 指定左侧文件所在的目录路径
2. `name` (string): 为左侧边栏这一项指定一个名字
3. `file_exclude_patterns` (array): 指定排除的文件
4. `folder_exclude_patterns` (array): 指定排除的目录
