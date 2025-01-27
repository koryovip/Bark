#### 推送使用次数限制 <!-- {docsify-ignore-all} -->
正常请求（HTTP状态码为200）无任何限制。<br>
但如果在5分钟内超过1000次错误请求（HTTP状态码为400 404 500）<b>IP会被 BAN 24小时</b> 

#### 时效性通知无效 
可以尝试<b>重启设备</b>来解决。

#### 无法保存通知历史，或下拉推送没有点击复制按钮无法复制
可以尝试<b>重启设备</b>来解决。<br />
因某些原因导致推送服务扩展（[UNNotificationServiceExtension](https://developer.apple.com/documentation/usernotifications/unnotificationserviceextension)）未能正常运行，执行通知保存的代码未能正常执行。

#### 自动复制推送失效
iOS 14.5 之后的版本因权限收紧，不能在收到推送时自动复制推送内容到剪切板。<br/>
可暂时先下拉推送或在锁屏界面左滑推送点查看即可自动复制，或点击弹出的推送复制按钮。

#### 默认打开通知历史列表
再次开启APP时，会跳转到上次打开的页面。<br />
只需退出APP时，停留在历史消息页面，再次打开APP时就是历史消息页面。

#### 推送 API 是否支持 POST 请求？
Bark支持 GET POST ,支持使用Json<br>
无论哪种请求方式，参数名都一样, 参考[使用教程](/tutorial#请求方式)

#### 推送特殊字符导致推送失败，比如 推送内容包含链接，或推送异常 比如 + 变成空格
这是因为整个链接不规范导致的问题，常发生在自己手动拼接URL时。<br>
拼接URL时，注意将参数进行URL编码 

```sh
# 例如
https://api.day.app/key/{推送内容}

# 如果{推送内容}是
"a/b/c/"

# 则最后拼接的URL是
https://api.day.app/key/a/b/c/
# 将找不到对应的路由，后端程序将返回404

# 应该将 {推送内容} url编码后再进行拼接
https://api.day.app/key/a%2Fb%2Fc%2F
```
如果是使用成熟的HTTP库时，参数都会被自动处理，无需自己手动编码。<br>
但如果是自己去拼接URL时，则需要特别注意参数中的特殊字符，**最好不管有没有特殊字符，无脑套一层URL编码**。

#### 如何保障隐私安全
参考[隐私安全](/privacy)
