## 练习平台
* [Hacker101](https://ctf.hacker101.com/ctf)

# SSH安全
* nmap -sV IP扫描-》敏感数据挖掘-》私钥泄漏/获取用户名尝试暴力破解

### Hacker101 Writeup
* A little something to get you started
没啥好说的，对于这种页面啥都没有的，查看源码和Networ口,即可发现Flag。
* Micro-CMS v1
四个flag，第一个为xss，新建一个topic在标题内插入script；第二个为访问权限漏洞，在edit内可访问到某一页面内包含了flag；第三位SQL注入，edit/1‘；第四在button内onclick插入一个xss