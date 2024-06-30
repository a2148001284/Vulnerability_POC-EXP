# 免责声明
该项目仅供合法的渗透测试以及爱好者参考学习，请各位遵守《中华人民共和国网络安全法》以及相应地方的法律，禁止使用该项目进行违法操作，否则自行承担相关责任！

# shiro反序列化漏洞综合利用

项目基于javafx,利用shiro反序列化漏洞进行回显命令执行以及注入各类内存马

1. 检出默认key (SimplePrincipalCollection) cbc/gcm
2. Tomcat/Springboot 回显命令执行
3. 集成CommonsCollectionsK1/K2
4. 通过POST请求中defineClass字节码实现注入内存马（Servlet实现参考哥斯拉内存马）
5. resources目录下shiro_keys.txt可扩展key

## 关于内存马
1. 某些spring环境以jar包启动写shell麻烦
2. 渗透中找目录很烦,经常出现各种写shell浪费时间问题
3. 无落地文件舒服

## bug修复
2020.11.08
1. 高低版本base64库不一致,目前使用org.apache.shiro.codec.Base64避免此问题

2020.11.10
1. 修复注入内存马都显示注入成功的错误。

2020.11.23
1. 忽略https证书错误。

2020.12.07
1. 添加AES GCM加密方式。
2. 修复内存马默认使用jdk1.8编译导致jdk版本不一致注入失败。

![](screenshot/screenshot.png)

![](screenshot/1.gif)

## 参考链接
- [ysoserial](https://github.com/zema1/ysoserial)
- [Godzilla](https://github.com/BeichenDream/Godzilla)
- [基于Tomcat无文件Webshell研究](https://mp.weixin.qq.com/s/whOYVsI-AkvUJTeeDWL5dA)
- [小姐姐带你看Shiro反序列化漏洞利用](https://mp.weixin.qq.com/s/WDmj4-2lB-hlf_Fm_wDiOg)
- [Java代码执行漏洞中类动态加载的应用](https://mp.weixin.qq.com/s?__biz=MzAwNzk0NTkxNw==&mid=2247484622&idx=1&sn=8ec625711dcf87f0b6abe67483f0534d)

