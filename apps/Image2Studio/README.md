# Image2Studio

成品级 Android image2 生图客户端，支持 OpenAI 兼容图片接口。

当前版本：`1.0.1` / `versionCode 2`

## 功能

- 默认中转站：`https://factory.pub`
- 默认模型：`gpt-image-2`
- API Key 本机输入，可选择是否保存
- 获取模型列表：`GET /v1/models`
- 文生图：`POST /v1/images/generations`
- 图生图 / 图片编辑：`POST /v1/images/edits`
- 支持多图参考，重复表单字段 `image`
- 支持比例预设和生成数量 1-4
- 兼容 `url`、`b64_json`、`b64` 图片响应
- 生成成功后自动持久化保存到 App 私有目录 `files/images`
- 历史记录显示缩略图，点击可预览
- 用户点击“保存当前结果到系统相册”后，才复制到系统相册 `Pictures/Image2Studio`
- 本机保存最近 20 条历史记录
- 请求日志自动隐藏 API Key

## 权限

- `INTERNET`：访问用户填写的图片生成接口。

无通讯录、短信、定位、相机等危险权限。

## 隐私

App 不内置、不上传、不外泄 API Key。用户选择“记住 API Key”时，仅保存到本机 SharedPreferences。
图生图只上传用户主动选择的图片。

## 源码

主源码：`app/src/main/java/cc/minis/image2studio/MainActivity.java`
