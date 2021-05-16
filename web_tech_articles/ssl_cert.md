### Openssl　秘密鍵からCSRや証明書への流れ

##### Step 1. 秘密鍵の作成：
```
$openssl version -a //バージョンの確認
LibreSSL 2.8.3
built on: date not available
platform: information not available
options:  bn(64,64) rc4(16x,int) des(idx,cisc,16,int) blowfish(idx) 
compiler: information not available
OPENSSLDIR: "/private/etc/ssl"

$openssl genrsa -out sample.key 2048 //秘密鍵作成
Generating RSA private key, 2048 bit long modulus
.....................................................................+++
........................+++
e is 65537 (0x10001)

$ls -la //鍵確認
total 8
drwxr-xr-x   3 xieheng  staff    96  5  8 01:20 .
drwxr-xr-x  37 xieheng  staff  1184  5  8 00:40 ..
-rw-r--r--   1 xieheng  staff  1679  5  8 01:20 sample.key

```

##### Step 2. 秘密鍵からパブリック鍵の抽出：  

秘密鍵からパブリック鍵を作成、パブリック鍵を通信相手に渡す。
- Input: 秘密鍵  
- Output：パブリック鍵  
  
```
$ openssl rsa -in sample.key -pubout -out sample_pub.key
writing RSA key

$ls -la
total 16
drwxr-xr-x   4 xieheng  staff   128  5  8 01:22 .
drwxr-xr-x  37 xieheng  staff  1184  5  8 00:40 ..
-rw-r--r--   1 xieheng  staff  1679  5  8 01:21 sample.key
-rw-r--r--   1 xieheng  staff   451  5  8 01:22 sample_pub.key
```

##### Step 3. CSRファイルの作成： 
秘密鍵からCSRを作成する
- Input: 秘密鍵
- Output: CSRファイル  
```
$openssl req -new -key sample.key -out sample.csr
You are about to be asked to enter information that will be incorporated
into your certificate request.
What you are about to enter is what is called a Distinguished Name or a DN.
There are quite a few fields but you can leave some blank
For some fields there will be a default value,
If you enter '.', the field will be left blank.
-----
Country Name (2 letter code) []:JP
State or Province Name (full name) []:TKY
Locality Name (eg, city) []:TKY
Organization Name (eg, company) []:ddd
Organizational Unit Name (eg, section) []:ppp
Common Name (eg, fully qualified host name) []:*.ddd.com
Email Address []:abc@ppp.com

Please enter the following 'extra' attributes
to be sent with your certificate request
A challenge password []:

$ls -la
total 24
drwxr-xr-x   5 xieheng  staff   160  5  8 01:25 .
drwxr-xr-x  37 xieheng  staff  1184  5  8 00:40 ..
-rw-r--r--   1 xieheng  staff  1021  5  8 01:25 sample.csr
-rw-r--r--   1 xieheng  staff  1679  5  8 01:21 sample.key
-rw-r--r--   1 xieheng  staff   451  5  8 01:22 sample_pub.key
```

必要な場合、CSRの内容を確認する：

```
$openssl req -text -in sample.csr -noout -verify
verify OK
Certificate Request:
    Data:
        Version: 0 (0x0)
        Subject: C=JP, ST=TKY, L=TKY, O=ddd, OU=ppp, CN=*.ddd.com/emailAddress=abc@ppp.com
        Subject Public Key Info:
            Public Key Algorithm: rsaEncryption
                Public-Key: (2048 bit)
                Modulus:
                    00:c8:b3:a4:f5:01:5e:4d:d2:ee:d3:ef:88:c0:d9:
                    da:e8:30:b8:4e:2d:58:f1:b3:4b:37:8c:6f:38:d6:
                    83:94:6f:07:0c:df:80:92:3d:8a:61:19:61:97:41:
                    35:77:ae:58:eb:ad:eb:62:bc:b6:14:ad:b2:8d:98:
                    25:90:ac:c3:a7:45:27:45:a2:d0:a0:d4:07:b3:45:
                    2b:fc:9a:c8:1c:ff:6d:1d:f9:d0:5f:6a:d4:ea:f8:
                    b1:33:b7:b7:bc:62:be:10:4f:0f:c9:09:49:67:87:
                    a2:bb:3c:5e:37:87:4d:8e:75:68:7c:25:86:83:ea:
                    45:bc:99:11:62:8c:6a:2d:13:0e:fc:cc:bb:57:72:
                    2c:9b:7c:21:be:89:74:4b:8b:29:f5:ee:d2:db:9c:
                    9d:45:6a:eb:42:24:8b:03:b3:2f:db:85:dd:4e:4d:
                    ab:6c:ca:85:10:00:bf:7e:a1:48:55:c7:01:a8:f5:
                    12:4f:25:b6:d7:24:c1:46:2f:6d:8e:5b:f0:22:d2:
                    f6:a7:af:bb:aa:22:99:ea:6f:88:9e:5b:70:78:4e:
                    b6:01:d4:6b:a7:07:a9:55:7b:e8:43:1d:4b:c1:94:
                    6e:e9:db:5e:b8:3a:a4:ce:7f:43:d4:37:4f:aa:bc:
                    c9:fa:ac:ef:98:72:11:9b:44:90:a9:43:53:95:a8:
                    b0:7b
                Exponent: 65537 (0x10001)
        Attributes:
            a0:00
    Signature Algorithm: sha256WithRSAEncryption
         94:eb:53:52:40:38:49:0e:c8:18:72:f1:df:7e:52:78:f5:96:
         50:7c:02:8f:3a:ae:d3:b7:75:6f:6d:25:5c:5a:65:b7:7b:a9:
         5d:0f:85:0a:3d:40:14:a2:c8:49:24:70:c8:23:7c:13:c7:bf:
         70:87:c5:33:22:ed:fd:4f:35:b9:ca:77:fd:8e:a3:24:2d:49:
         94:f7:78:e6:e3:8e:45:7e:d2:65:4c:60:38:e8:1b:11:22:d3:
         b7:52:1d:71:c4:69:c7:47:35:28:fc:29:d8:af:c4:72:4f:d7:
         35:b7:2a:01:d8:24:06:ed:3b:90:aa:b4:93:db:3e:46:93:af:
         38:1b:a8:21:90:f3:e4:11:54:b5:52:04:24:07:26:60:35:e1:
         f2:5a:81:4b:a4:d5:bf:6e:be:93:30:bf:fa:7a:82:02:b3:35:
         d6:ae:e9:19:e0:26:50:f3:68:63:af:fb:e2:96:28:35:49:72:
         de:b8:8c:79:d8:f4:b1:69:45:ae:fb:14:1b:9d:3f:0e:69:7d:
         96:fa:08:95:2d:88:36:55:ef:19:d3:be:63:87:bc:c3:d8:b7:
         a3:2c:a5:64:c8:98:35:2d:b8:cb:7c:85:eb:2b:73:85:68:5f:
         a2:cf:cd:86:a8:cc:78:b4:36:6c:55:a7:ae:80:ee:28:80:2a:
         4a:0e:4a:3f
```

組織名、国名など情報は正しいか確認する、間違っている場合は再作成する。

##### Step 4. 署名証明書の作成：
通常はCSRをCAサーバへ渡し、証明書を発行してもらう、テストのため、Self-signed 証明書を作成する。　
- Input: CSRファイル　
- 署名鍵: 秘密鍵　
- Output: 署名証明書  

```
$openssl x509 -in sample.csr -out sampole.crt -req -signkey sample.key -days 90 
Signature ok
subject=/C=JP/ST=TKY/L=TKY/O=ddd/OU=ppp/CN=*.ddd.com/emailAddress=abc@ppp.com
Getting Private key
$ls -la //確認：crtファイル作成されたこと
total 32
drwxr-xr-x   6 xieheng  staff   192  5  8 01:27 .
drwxr-xr-x  37 xieheng  staff  1184  5  8 00:40 ..
-rw-r--r--   1 xieheng  staff  1021  5  8 01:25 sample.csr
-rw-r--r--   1 xieheng  staff  1679  5  8 01:21 sample.key
-rw-r--r--   1 xieheng  staff   451  5  8 01:22 sample_pub.key
-rw-r--r--   1 xieheng  staff  1241  5  8 01:27 sampole.crt
```

###### reference:
[OpenSSL Step By Step Tutorial | How to Generate Keys, Certificates & CSR Using OpenSSL](https://www.youtube.com/watch?v=wzbf9ldvBjM)
[SSL/TLS协议详解](https://cshihong.github.io/2019/05/09/SSL%E5%8D%8F%E8%AE%AE%E8%AF%A6%E8%A7%A3/)
