# Image2Studio

成品级 Android image2 生图客户端，支持 OpenAI 兼容图片接口。

当前版本：`1.1.0` / `versionCode 4`

## v1.1.0 重点

- UI 重构为软件式工作台：顶部品牌状态卡 + 文生图 / 图生图 / 历史 / 设置四个模式页。
- 开始文生图、开始图生图、获取模型时，按钮会变成处理中并禁用，结束后恢复。
- 按 image2 skill 规则增加清晰度：`auto`、`高清`、`真4K`。
- 真4K size 映射：
  - 16:9 → `3840x2160`
  - 9:16 → `2160x3840`
  - 1:1 → `2880x2880`
  - 4:3 → `3200x2400`
  - 3:4 → `2400x3200`
  - 其他比例 → `auto` 并把比例写入 prompt
- 文生图 JSON 传 `size` 字段。
- 图生图 multipart 传 `size` 字段。
- 历史记录可预览、载入、保存本条到系统相册。

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
- 用户点击保存时，复制到系统相册 `Pictures/Image2Studio`
- 请求日志自动隐藏 API Key

## 权限

- `INTERNET`：访问用户填写的图片生成接口。

无通讯录、短信、定位、相机、相册读写等危险权限。

## 隐私

App 不内置、不上传、不外泄 API Key。用户选择“记住 API Key”时，仅保存到本机 SharedPreferences。
图生图只上传用户主动选择的图片。

## 源码

主源码：`app/src/main/java/cc/minis/image2studio/MainActivity.java`
