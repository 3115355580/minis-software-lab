# Image2Studio

成品级 Android image2 生图客户端，支持 OpenAI 兼容图片接口。

当前版本：`2.2.2` / `versionCode 12`

## v2.2.2

- 当前结果支持直接分享 App 内部已持久化图片，不再要求先保存到系统相册。
- 新增内部图片 `ContentProvider`，通过 `content://cc.minis.image2studio.share/...` 给系统分享面板临时授权。
- 保留“保存到相册”作为复制到系统相册的独立操作。
- 底部导航保持实体不透明 TabBar。
- 图生图参考图支持缩略图预览和单独删除。

## 参数规则

比例：`Auto`、`16:9`、`9:16`、`1:1`、`4:3`、`3:4`

清晰度：`Auto`、`4K`

## 权限

- `INTERNET`

无通讯录、短信、定位、相机、相册读写等危险权限。
