# 如何安装自定义 GApp

1. 构建没有gapps的WSA让脚本下载需要的文件

     `./build.sh --gapps-brand none`
1.
     - 对于 OpenGApps

         将自定义 OpenGApps 放入“下载”文件夹并重命名为“OpenGApps-{arch}-{variant}.zip”（例如“OpenGApps-x64-pico.zip”）
     - 对于 MindTheGapps

         将自定义 MindTheGapps 放入“下载”文件夹并重命名为“MindTheGapps-{arch}.zip”（例如“MindTheGapps-x64.zip”）
1. 离线搭建WSA

     `./build.sh --offline --gapps-brand {brand} --gapps-variant {variant}`
