## Google Authenticator 激活协议

### 一、概述

- Google Authenticator：谷歌的app，激活后可以生成动态密码
- 宁盾令牌：宁盾的app，激活后可以生成动态密码

- 第二章：Google激活协议，Google官方的标准协议
- 第三章：宁盾增强版协议，在Google协议上进行了增强

### 二、Google激活协议

> 此二维码是一个示例，使用《Google Authenticator》或《宁盾令牌》扫描此二维码，可以激活令牌

![Google](https://github.com/Ningdun/Activation-code-protocol/blob/master/Google.png)

> 二维码内容如下

```
otpauth://totp/ACME%20Co:john.doe@email.com?secret=HXDMVJECJJWSRB3HWIZR4IFUGFTMXBOZ&issuer=ACME%20Co&algorithm=SHA1&digits=6&period=30
```

| 参数            |          | 说明                                         |
| --------------- | -------- | -------------------------------------------- |
| otpauth://totp/ |          | 时间型令牌的前缀                             |
| secret          |          | 令牌的种子<br>随机生成byte[]，然后Base32编码 |
| issuer          | 可选参数 | 发行人                                       |
| algorithm       | 可选参数 | 目前Google默认为SHA1                         |
| digits          | 可选参数 | 动态密码的长度                               |
| period          | 可选参数 | 动态密码的变化周期（秒）                     |

> 谷歌官方说明 https://github.com/google/google-authenticator/wiki/Key-Uri-Format

### 三、宁盾增强版协议

> 请先看第二章

> Google Authenticator也可以扫描根据此协议生成的二维码，但是增强功能不生效

| 参数           |          | 说明                                                         |
| -------------- | -------- | ------------------------------------------------------------ |
| nd_noWxToken   | 可选参数 | 默认值false<br>false：《app版本的宁盾令牌》和《微信小程序版本的宁盾令牌》可以使用此激活码激活<br>true：《app版本的宁盾令牌》可以使用此激活码激活 |
| nd_noCloudSync | 可选参数 | 默认值false<br>false：令牌可以备份到云<br>true：禁止备份此令牌到云 |
| nd_distributor | 可选参数 | 经销商代码，从宁盾认证后获取到的，也可以随意填写，也可以不写 |

