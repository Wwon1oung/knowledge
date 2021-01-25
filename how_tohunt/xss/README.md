# 反射的Xss方法

使用arjun和ParamSpider  
检查Javascript文件或html源文件中是否存在隐藏或未使用的变量  
使用gf模式过滤参数，并将其存储在新文件中。 


# 存储的Xss方法
在网站上的用户名，名称，地址，电子邮件等字段中注册      
在个人资料图片的文件名以及图片的源文件    
在目标站点上的任何地方尝试“评论”部分    
尝试在页面上反映出来并可以被其他用户看到的每个输入字段     
尝试使用您的名称+ xss有效负载进行注册，这可能会导致存储xss:   
* 对于每个输入字段     
尝试获得<a href=#>test</a>一个实体    

# 盲Xss
* Review forms
* 联系我们页面
* 密码
* 电子商务网站的地址字段
* 进行支付时的名字或姓氏字段
* Set User-Agent to a Blind XSS payload. You can do that easily from a proxy such as Burpsuite.
* 日志查看器
* 反馈页
* 聊天应用程序
* 任何需要用户调节的应用程序

