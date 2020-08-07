## SQL注入
### 判断能否sql注入
* 提交单引号 ```id=1'```
* and大法和or大法 
```
id=2 and 1=1
id=2 or 1=1 
```
* 加减法
```
id=1+1
```
### 数据库权限判断

### 猜字段个数
* 在注入点后面加order by x
### Union all
union all只是简单的将两个结果合并后就返回。这样，如果返回的两个结果集中有重复的数据，那么返回的结果集就会包含重复的数据了。

### 显错注入和盲注
*  显错注入，即带回显错误提示，可利用联合查询union select来爆出更多信息。
*  盲注，没有任何信息返回，一般可以利用时间sleep()来判断查询成功与否，使用and来盲猜数据库名，表名
### MSSQL
*  is_srvrolemember ('sysadmin')函数是用来判断当前的数据用户是否属于管理员组权限
---
## 高级绕过方法
### 利用字符串转换来绕过php检测
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