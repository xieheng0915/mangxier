## github + jenkins + Azure インテグレーション

###### 1.Push jenkins to Azure
- 前提条件：  
    すでに docker hub に login 済み

- 1.1) Mac - terminal で context を作成：
```
docker context create aci myacicontext //"myacicontext"は他の名前に切り替えで良い
docker context ls // 確認
```
上記、複数のsubscription、resource-groupがある場合に自動にCommandlineで聞かれて選択できる。

- 1.2) プッシュjenkins to azure
```
dockder --context myacicontext run -p 8080:8080 -p 5000:5000 jenkins/jenkins:lts
```
しばらく待つと、portal でazure container instance を確認する
![azure portalでjenkins containerを確認](jenkins_source/../jenkins_sources/after-pushed-jenkins-to-azure.png)　　

上記、jenkins serverは global IP：(http://52.188.36.102:8080/)でアクセスできる。  

- 1.3) Terminal で　確認方法：  
```
docker context use myacicontext
docker ps //azure上動いているコンテナーを確認できる
CONTAINER ID        IMAGE                 COMMAND             STATUS              PORTS
upbeat-bell         jenkins/jenkins:lts  
docker logs upbeat-bell // jenkinsの初期パスワードはログからチェックする
```

###### 2.Jenkins preparation
- 2.1) Jenkins 初期化　
  初期パスワードは上記1.3より確認とCopy＋Paste、Default Pluginを自動化インストールする

- 2.2) Github Pluginのインストール 
  Dashboard -> Manage Jenkins -> Manage Plugins  
  ![find plugins](jenkins_sources/add-github-plugin.png)  
  Search bar -> github -> github integration, auto restart check-box を選択しておく  
  ![install github integration plugin](jenkins_sources/add-github-plugin-02.png)
　
　Jenkins restart 済みしておく　　

###### 3.Integration with github
- 3.1) jenkins でnew view,input view name, -> select Freestyle ->「OK」
  github project -> project url (on github) 
  source code managent -> git -> repositories -> github project repo 
  ![configuration 01](jenkins_sources/configuration-01.png)  
  Scroll ...  
  Build Triggers -> GitHub hook trigger for GITScm polling   
  ![configuration 02](jenkins_sources/configuration-02.png)  

  - 3.2) Github でwebhookを作成　　
  github -> CI/CD 対象プロジェクト -> Settings -> Webhooks 
  Payload URL: jenkins url + /github-webhook/   
  Content type: applicaiton/json 
  Pushだけ通知することに　　
  ![create a webhook](jenkins_sources/create-a-webhook.png)  
  ![after created](jenkins_sources/afterwebhookcreated.png)  

  - 3.3) test 
    + repo で　ファイルを編集、Push
    + jenkinsで自動反映とBuild
   ![auto-detect-push](jenkins_sources/autopull-with-webhook.png) 
    + Build 済み
   ![after-auto-building](jenkins_sources/afer-auto-build.png)