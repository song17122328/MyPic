核心思路
截图保存到本地 → 2. 自动上传到 GitHub → 3. 替换 Typora 图片链接为 GitHub 的 CDN 链接。

具体步骤
1. 配置 GitHub 图床
在 GitHub 上创建一个仓库（如 my-images），用于存放图片。

生成 GitHub Personal Access Token（生成教程），勾选 repo 权限。

2. 使用工具自动上传图片
推荐通过 PicGo + GitHub 插件 实现自动上传：

下载 PicGo（支持 Windows/macOS）：

官网：https://github.com/Molunerfinn/PicGo

配置 PicGo 的 GitHub 图床：

打开 PicGo → 图床设置 → GitHub 图床 → 填写以下信息：

仓库名: 你的用户名/my-images
分支: main
Token: 你的GitHub Token
存储路径: img/  （可选，用于分类）
自定义域名: https://cdn.jsdelivr.net/gh/你的用户名/my-images@main
保存配置，设为默认图床。

3. 配置 Typora 自动调用 PicGo
打开 Typora → 偏好设置 → 图像：

选择 “上传图片” 功能。

上传服务选 PicGo (app)，并填写 PicGo 的安装路径（如 /Applications/PicGo.app）。

勾选 “插入图片时自动上传” 和 “对本地位置的图片应用上述规则”。

4. 截图并插入 Typora
用系统截图工具（如 macOS 的 Shift+Cmd+4 或 Windows 的 Win+Shift+S）截图后，直接粘贴到 Typora。

Typora 会自动：

将图片保存到本地（可选，可在设置中关闭本地保存）。

调用 PicGo 上传图片到 GitHub 仓库。

替换文档中的图片链接为 jsDelivr CDN 链接（如 https://cdn.jsdelivr.net/gh/你的用户名/my-images@main/img/xxx.png）。

验证效果
在 Typora 中插入图片后，检查文档中的图片地址是否变为 jsdelivr.net 的链接。

分享文档时，图片会通过 CDN 加载，无需依赖本地文件。

注意事项
GitHub 仓库需设为 Public：jsDelivr 仅加速公开仓库。

图片大小限制：GitHub 单文件建议 ≤ 25MB。

备份本地图片：可在 Typora 设置中保留本地副本以防上传失败。

如果需要更自动化（如截图后直接触发上传），可搭配 Alfred（macOS） 或 AutoHotkey（Windows） 进一步优化流程。
