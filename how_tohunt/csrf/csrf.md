-更改请求方法[POST=>GET]
-移除令牌，并提供一个空参数
-通过删除请求并使用该令牌来复制未使用的有效令牌
-使用自己的CSRF令牌将其提供给受害者
-将值替换为具有相同长度的标记的值
-对令牌进行反向工程
-通过HTML注入提取令牌
-从非格式“Content Type:application/json”或“Content Type:application/x-url-encoded”切换到“Content Type:Form multipart”`
-绕过正则表达式
如果网站正在寻找“银行网站“在referer URL中，也许”bank.com.攻击者.com“或”http://www.com/bank.cn.com”将起作用。
-删除referer头（将此<meta name=“referer”content=“no referer”>添加到有效负载或html代码中）








