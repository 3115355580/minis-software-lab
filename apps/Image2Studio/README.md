# Image2Studio

成品级 Android image2 生图客户端，支持 OpenAI 兼容图片接口。

当前版本：`1.1.2` / `versionCode 6`

## v1.1.2 修复

- 按用户要求精简比例，只保留实测 4K 列表：
  - `Auto`
  - `16:9`
  - `9:16`
  - `1:1`
  - `4:3`
  - `3:4`
- 清晰度只保留：
  - `Auto`
  - `4K`
- `Auto` 清晰度：不传 `size` 字段，避免中转站断连。
- `4K` 清晰度：按比例传实测尺寸：
  - 16:9 → `3840x2160`
  - 9:16 → `2160x3840`
  - 1:1 → `2880x2880`
  - 4:3 → `3200x2400`
  - 3:4 → `2400x3200`
  - 比例 Auto + 4K → 默认 `2880x2880`

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
- 历史记录可预览、载入、单条保存到系统相册
- 请求日志自动隐藏 API Key

## 权限

- `INTERNET`：访问用户填写的图片生成接口。

无通讯录、短信、定位、相机、相册读写等危险权限。

## 隐私

App 不内置、不上传、不外泄 API Key。用户选择“记住 API Key”时，仅保存到本机 SharedPreferences。
图生图只上传用户主动选择的图片。
