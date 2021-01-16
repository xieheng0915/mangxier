## Angular/React/Vue　プラットフォームの比較
===================================================

1. 思想、哲学  
   |  Angular  |  React  |  Vue
   | :---:  | :---:  | :---: 
   |  性能豊富  |  最小性能セット、UI向け性能強化 | Angular と　React の間  
   |  PlatformよりFramework  |  FrameworkよりLibrary  |  Framework, Code重視  
   |  Code以外、CLI、PWAなど充実  |  第三者のツールでRoutingとhttpclientなど機能補足必要  |  Code重視が、CLI機能やroutingなど機能も提供
   
2. 特徴
   ![Feature comparation](sources/performance_comp.jpg)
3. 学習コスト  
   |  Angular  |  React  |  Vue  
   | :---:  | :---:  | :---: 
   | かなり複雑な構造 | やや複雑な構造  |  必要に応じて構造変更可能　　
   | TypeScript 必須 | Javascript + JSX/TSX | Javascript のみ　　
   | HTML,TS 分ける構造  | JS+HTML 混在  |  JS, HTML 分ける構造　
   | **学習コスト: 高**　| **学習コスト：中** | **学習コスト：低**

4. 性能  
   Bundle Size: Angular > React > Vue  
   1. StartUp Speed:  
   ![Startupスピード](sources/startup_metrics.png)
   1. Memory Allocation:  
   ![Memory Allocation](sources/memory_allocation.png)
5. 人気度  
   下記データはGoogle上サーチ回数の比較結果:
   ![google search result](sources/framework_trends.png)
6. 将来性  
   下記はGitHub上Starをつける数  
   ![github star history](sources/frameworks_star_history.png)
7. その他情報  
   Angular 初回リリース：2010   
   React 初回リリース： 2013  
   Vue 初回リリース： 2014  

　　Angular community の開発者はその他のFWに徐々に流出している、人気度は下がっている状況。
     
   

### 結論

結論ありません。自分のニーズに合わせて選びましょう！

##### Ref：
 
1. [React, Angular or Vue: Choosing the Right Framework for Your Project](https://leanylabs.com/blog/react-angular-vue/)
2. [Youtube: create same app in vue and react and compare them](https://medium.com/javascript-in-plain-english/i-created-the-exact-same-app-in-react-and-vue-here-are-the-differences-e9a1ae8077fd)

