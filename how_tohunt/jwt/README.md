以.分隔
* 标头
 {
   "alg" : "HS256",
   "typ" : "JWT"
 } 

* 有效载荷
> { 
 "loggedInAs" : "admin",
 "iat" : 1422779638 
> }
* 签名
> HMAC-SHA256
( 
 secret,
 base64urlEncoding(header) + '.' + 
 base64urlEncoding(payload) 
)

* 将alg更改为null  
例  
{
 "alg" : "NONE",  
 "typ" : "JWT"  
}
Note;;////--remove the signuature  
You can also use none,nOne,None,n0Ne

* 更改有效负载，例如    
Payload   	
{
 "loggedInAs" : "admin",  
 "iat" : 1422779638  
}  

##### 在这里将用户更改为管理员
1. 首先将完整令牌或11个令牌的每个部分解码为base64
2. 更改有效负载使用jwt Web令牌burp
3. 更改rs256到sh256
4. 签名不能更改，请删除或修改，
5. 暴力破解hs256中的密钥，因为它使用相同的密钥来签名和验证，意味着publickey = private key

###  其他方法
1. 创建帐户  
2. 检查令牌  
3. Base64解码报头  
4. 如果有任何Kid=参数，那么您可以找到一些bug  
5. 使用这个参数你也可以找到目录遍历：  
6. Change that kid= parameter with you directory traversal payload  
7. 更改负载{“user”：“admin”}  
8. 创建一个python脚本，生成一个漏洞利用令牌。  
9. 把那个令牌放进去，然后重新加载页面  
10. 完成



