# XML外部实体。

## 方法
1. 将内容类型从“ application / json” /“ application / x-www-form-urlencoded”转换为“ applcation / xml”。
2. 文件上载允许docx / xlcs / pdf / zip，解压缩包，然后将恶意的xml代码添加到xml文件中。
3. 如果图片上传中允许使用svg，则可以在svgs中注入xml。
4. 如果该网络应用提供了RSS供稿，请将您的恶意代码添加到RSS中。
5. 对/ soap api进行模糊测试，某些应用程序仍在运行soap api
6. 如果目标Web应用允许进行SSO集成，则可以在SAML请求/响应中注入恶意xml代码
