# SQL注入
---
## 类别
### 联合查询注入
### 报错注入
1. updatexml()
2. floor()
3. exp()
### Bool盲注
### 时间盲注
1. sleep()
2. benchmark()
### 二次注入
---
## 注入点
#### GET参数
#### POST注入
#### User-Agent注入
#### Cookies注入
---
## 绕过
### 过滤关键字
1. 无递归过滤时select --> selselectect
2. 大小写过滤select --> SelECt
3. 十六进制过滤select --> selec\x74
4. 双重url编码过滤 or --> %25%36%66%25%37%32
### 过滤空格
1. 注释绕过 #、--、//、/**/、；%00
```
select/**/username/**/from/**/user
```
2. URl编码绕过
```
通过二次url编码绕过，%20 --> %2520
```
3. 通过空白字符绕过，在数据库中存在一些空白字符
4. 特殊符号(反引号，加号)
```
select`user`,password`from..
```
5. 科学计数法
```
select user,password from users where user_id=0e1union select 1,2...
```

---
### 猜字段个数
* 在注入点后面加order by x
### Union all
union all只是简单的将两个结果合并后就返回。这样，如果返回的两个结果集中有重复的数据，那么返回的结果集就会包含重复的数据了。

### MSSQL
*  is_srvrolemember ('sysadmin')函数是用来判断当前的数据用户是否属于管理员组权限
---
## 高级绕过方法
### 利用字符串编码来绕过php检测
Mysql字段的字符集和php mysqli客户端设置的字符集不相同
例如佬这个汉字的UTF-8编码是xE4xBDxAC
我们依次使用xE4,xE4xBD,xE4xBDxAC作为参数传入
能够发现前两个都可以成功，但是第三个(佬的完整编码)会引发一个错误
这是因为在utf8转换为latin1时,latin1并不支持汉字,而之前并没有报错是因为编码不完整,Mysql进行转换时自动将其忽略
```
if ($username === 'admin') {
    if ($_SERVER['REMOTE_ADDR'] !== '127.0.0.1') {
        die('Permission denied!');
    }
}
$result = $mysqli->query("SELECT * FROM z_users where username = '{$username}' and password = '{$password}'");
```
此时传入username=admin%c2，php的检测if ($username === 'admin')自然就可以绕过的，在mysql中可以正常查出username='admin'的结果。