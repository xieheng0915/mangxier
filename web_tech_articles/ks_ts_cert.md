### Keystore、TrustStoreと通信処理

- one-way SSL: 
    - Keystore: Server side
    - Truststore: Client side
- two-way SSL: 
    サーバとサーバ間の通信のため、両方Keystore/Truststoreを持つ


##### 1. Generate keystore and certificate (サンプル)
```
% keytool -genkey -alias spedia -keyalg RSA -keystore "/Users/xieheng/gitspace/openssl/keystore/spedia.jks"
キーストアのパスワードを入力してください:  
新規パスワードを再入力してください: 
姓名は何ですか。
  [Unknown]:  heng
組織単位名は何ですか。
  [Unknown]:  local
組織名は何ですか。
  [Unknown]:  tky
都市名または地域名は何ですか。
  [Unknown]:  kanagawa
都道府県名または州名は何ですか。
  [Unknown]:  kawasaki
この単位に該当する2文字の国コードは何ですか。
  [Unknown]:  81
CN=heng, OU=local, O=tky, L=kanagawa, ST=kawasaki, C=81でよろしいですか。
  [いいえ]:  y

90日間有効な2,048ビットのRSAのキー・ペアと自己署名型証明書(SHA256withRSA)を生成しています
	ディレクトリ名: CN=heng, OU=local, O=tky, L=kanagawa, ST=kawasaki, C=81
% ls
spedia.jks
```
↑上記keystoreのjksファイルは作成された。

下記、keystoreからcertificateを作成、PublicKeyはCertificateに含まれている。
```
% keytool -export -alias spedia -file "/Users/xieheng/gitspace/openssl/keystore/spedia_pub_cert.cer" -keystore "/Users/xieheng/gitspace/openssl/keystore/spedia.jks"
キーストアのパスワードを入力してください:  
証明書がファイル</Users/xieheng/gitspace/openssl/keystore/spedia_pub_cert.cer>に保存されました
% ls
spedia.jks		spedia_pub_cert.cer
% ls -la
total 16
drwxr-xr-x  4 xieheng  staff   128  5  8 23:37 .
drwxr-xr-x  7 xieheng  staff   224  5  8 23:29 ..
-rw-r--r--  1 xieheng  staff  2567  5  8 23:35 spedia.jks
-rw-r--r--  1 xieheng  staff   871  5  8 23:37 spedia_pub_cert.cer
```

次へ：
[Openssl　秘密鍵からCSRや証明書への流れ](./ssl_cert.md)

