

# appdmg 应用



// 打包命令：
`appdmg ./dists/pack.json ./dists/MyApp.dmg`



- pack.json文件内容：

`{
    "title": "MyApp",
    "icon": "icon.icns", // 图标
    "background": "background.png", // 背景图片
    "contents": 
    [
        { "x": 448, "y": 344, "type": "link", "path": "/Applications" },
        { "x": 192, "y": 344, "type": "file", "path": "./MyApp.app" }
    ],
    "window": 
    {
        "size":
        {
           "width": 640,
           "height": 480
        }
    },
    "format": "UDBZ", // 还有很多种，具体看appdmg的官方文档
 }`
###这些坐标以及大小需要自己不断的尝试
