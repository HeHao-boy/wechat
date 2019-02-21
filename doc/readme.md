
## 相关概念

* access_token
* openid

## 接收普通消息

* 支持类型：文本、语音、图片、位置、视频、小视频、链接
* 需要公网服务器
* 语音、图片、位置、视频、小视频收到的是MediaId，需要单独下载: `Service\MaterialService::downFile()`
	
## 被动回复普通消息
	
* 接收到普通消息后5秒内立即做出回应
* 只能在接收消息时响应一次
* 支持回复文本、图片、图文、语音、视频、音乐(实现了`Contract\ReplyMessage`接口的类)
* 回复图片等多媒体消息时需要预先上传临时素材或永久素材:`Service\MaterialService::uploadFileTemporary()`
	
	
## 客服消息

用户发生以下行为后的48小时内，允许主动发送消息给用户:
	
	1、用户发送信息
	2、点击自定义菜单（仅有点击推事件、扫码推事件、扫码推事件且弹出“消息接收中”提示框这3种菜单类型是会触发客服接口的）
	3、关注公众号
	4、扫描二维码
	5、支付成功
	6、用户维权

支持如下类型：

	文本消息（Message\Text)
	图片消息 (Message\Image）
	语音消息 (Message\Voice）
	视频消息 (Message\Video）
	音乐消息 (Message\Music）
	发送图文消息（点击跳转到外链） (Message\News）
	发送图文消息（点击跳转到图文消息页面） (Message\MpNews）
	发送卡券(Message\Wxcard)

调用 `Service\MessageService::send()`
	
	
## 群发消息

订阅号每天一条群发权限，服务号每自然月4条

全体或某个分组
	
	MessageService::sendAll()

OpenID列表群发(限认证服务号)

	MessageService::sendAllWithOpenids()
	
## 菜单管理

自定义菜单最多包括3个一级菜单，每个一级菜单最多包含5个二级菜单

测试时可以尝试取消关注公众账号后再次关注，可以看到新创建后的效果

	1、click：可以通过自定义的key值与用户进行交互
	2、view：打开在按钮中填写的网页URL
	3、scancode_push：微信客户端将调起扫一扫工具，完成扫码操作后显示扫描结果（如果是URL，将进入URL），且会将扫码的结果传给开发者
	4、scancode_waitmsg：微信客户端将调起扫一扫工具，将扫码的结果传给开发者，然后弹出“消息接收中”提示框
	5、pic_sysphoto：微信客户端将调起系统相机，会将拍摄的相片发送给开发者
	6、pic_photo_or_album：微信客户端将弹出选择器供用户选择“拍照”或者“从手机相册选择”
	7、pic_weixin：微信客户端将调起微信相册
	8、location_select：将选择的地理位置发送给开发者的服务器
	9、media_id：微信服务器会将开发者填写的永久素材id对应的素材下发给用户
	10、view_limited：微信客户端将打在按钮中填写的永久素材id对应的图文消息URL，只支持图文消息

## 生成带参数的二维码

临时 永久
	
## 接收事件推送

	1 关注/取消关注事件
	2 扫描带参数二维码事件
	3 上报地理位置事件
	4 自定义菜单事件
	5 点击菜单拉取消息时的事件推送
	6 点击菜单跳转链接时的事件推送

## 用户管理

获取用户列表

用户标签管理


## 微信网页开发

微信网页授权

微信JS-SDK说明文档


## 支付与红包

