

# appdmg 应用



// 打包命令：
`appdmg ./dists/pack.json ./dists/MyApp.dmg`



- pack.json文件内容：

`{`<br/>`
    "title": "MyApp",`</br>`
    "icon": "icon.icns",` // 图标</br>`
    "background": "background.png",` // 背景图片</br>`
    "contents":` </br>`
    [`</br>`
        { "x": 448, "y": 344, "type": "link", "path": "/Applications" },`</br>`
        { "x": 192, "y": 344, "type": "file", "path": "./MyApp.app" }`</br>`
    ],`</br>`
    "window": `</br>`
    {`</br>`
        "size":`</br>`
        {`</br>`
           "width": 640,`</br>`
           "height": 480`</br>`
        }`</br>`
    },`</br>`
    "format": "UDBZ", // 还有很多种，具体看appdmg的官方文档`</br>`
 }`</br>
###这些坐标以及大小需要自己不断的尝试
