# 个人工作台 Android 版

这是由你提供的 `个人工作台.html` 封装成的原生 Android WebView 工程。

## 特性
- 应用名：个人工作台
- 包名：com.personal.workbench
- 版本：1.0
- 最低 Android API：23
- HTML 内置在 APK 中，不需要静态托管
- JavaScript / localStorage 已开启
- INTERNET 权限已添加，用于原 HTML 的 GitHub / Hacker News 资讯请求
- HTTP/HTTPS 外部链接交给手机浏览器打开

## 在 Android Studio 中生成可安装 APK
1. 安装最新版 Android Studio。
2. 用 Android Studio 打开本文件夹 `PersonalWorkbench_AndroidStudio`。
3. 等待 Gradle Sync 完成；若提示安装 Android SDK 36，请接受安装。
4. 菜单选择：Build → Build App Bundle(s) / APK(s) → Build APK(s)。
5. Debug APK 通常生成在：
   `app/build/outputs/apk/debug/app-debug.apk`
6. 把 APK 发送到 Mate 60，允许“安装未知应用”后安装即可。

## 正式长期使用
若以后要持续升级并保留相同应用身份，请用：
Build → Generate Signed App Bundle or APK → APK
创建并永久保存自己的 keystore。以后每个版本都用同一个 keystore 签名。

## 数据说明
工作台仍使用 WebView 的 localStorage 保存数据。
覆盖升级通常不会清空数据，但“卸载应用”或“清除应用数据”会删除本地数据。
长期使用建议后续增加 JSON 导出/导入备份功能。

## 不装 Android Studio：用 GitHub 在线生成 APK
工程已附带 `.github/workflows/build-apk.yml`。

1. 新建一个 GitHub 仓库，把本工程内容上传到仓库根目录。
2. 打开仓库的 Actions 页面。
3. 选择 `Build Android APK`。
4. 点击 `Run workflow`。
5. 构建完成后，在该次运行页面的 Artifacts 下载 `PersonalWorkbench-debug-apk`。
6. 解压即可得到 `app-debug.apk`。
