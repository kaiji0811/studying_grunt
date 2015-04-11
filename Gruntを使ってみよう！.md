##Gruntを使ってみよう！  

それでは、Gruntの導入から見ていきたいと思います。
  1. grunt-cliをインストール
  1. package.jsonを作成
  1. Grunt本体、その他プラグインをインストール
  1. Gruntfile.jsを作成
  1. Gruntを起動

###1.grunt-cliをインストール  
grunt-cliとは、コマンドラインからGruntを使用するためのツールのことです。  
以下のコードを実行し、インストールを行います。  

```
$ npm install -g grunt-cli
```

これでgrunt-cliはインストールされました。  

###2.package.jsonを作成  
package.jsonはNode.jsのプロジェクトにおいて、そのプロジェクトの名称やバージョン、依存するモジュールを書いておくためのファイルです。詳しくはググりましょう！検索検索ゥ！  
package.jsonはコマンドラインから作成する事ができます。  
Node.jsを使用したいプロジェクトのディレクトリに移動し、以下のコードを実行してみましょう。  

***package.jsonを作成***  
```
$ npm init
```  

コマンドを入力すると色々聞かれますが、とりあえずはエンターを押していけば自動で
情報が記述されたpackage.jsonが生成されます。  

```
{
  // package.jsonのサンプル
  "name": "プロジェクトの名前",
  "version": "プロジェクトのバージョン（0.0.1など）",
  "description": "プロジェクトの説明",
  "author": "作者名",
  "license": "ライセンス",
  "dependencies": {
    　// パッケージの実行に必要なパッケージの定義
    },
  "devDependencies": {
    //パッケージの開発に必要なパッケージの定義
  }
}
```  

###3.Grunt本体、その他プラグインをインストール  
Gruntをコマンドラインで使用するgrunt-cliはインストールされましたが、  
まだ肝心のGruntがインストールされていません。  
以下のコードを実行しインストールしてみましょう。  

```
npm install grunt --save-dev
```  

これでGruntがインストールされました。  
``--save-dev``をオプションにつけることで、package.jsonにプラグインの情報を記載してくれます。  
基本的には``--save-dev``をつけてインストールするようにしましょう。  
  
また、プラグインをインストールする際にも``npm install``を使用します。  
では、grunt-contrib-connectというローカルサーバーを立てるためのプラグインと、
ファイルの変更などを監視するgrunt-contrib-watchをインストールしてみましょう。

***プラグインをインストール***  

```
$ npm install grunt-contrib-connect grunt-contrib-watch --save-dev
```  

###3.Gruntfile.jsを作成  
Gruntfile.jsとは、Gruntの設定を行うjsファイルです。  

***Gruntfile.jsの構成***  

```
module.exports = function(grunt) {
    // gruntの設定をここに書く
};
```  

Gruntに関する全てのコードは、上記の関数内に記述する必要があります。
以下のコードをGruntfile.jsとして保存してみましょう。  

***Gruntfile.js サンプル***

```
module.exports = function(grunt){
 
  pkg: grunt.file.readJSON('package.json'),  //package.jsonを取得
 
  grunt.initConfig({      //grunt.initConfigの中にタスクの設定を記述する
    connect: {
      server: {
          options: {
              port: 9000,
              base: ''
          }
      }
    },
    watch: {
      options: {
          livereload: true
      },
      html: {
          files: ['*.html'],
          tasks: ['']
      }
    }
  });
 
  // loadNpmTasksを使用して、プラグインを読み込む
  grunt.loadNpmTasks('grunt-contrib-connect');
  grunt.loadNpmTasks('grunt-contrib-watch');
 
  //defaultと設定することで、登録しているタスクを実行する。
  grunt.registerTask('default', ['connect', 'watch']);
 
};
```

これでgrunt-contrib-connectというプラグインによって簡易サーバーが起動し、  
watchで設定しているファイルの監視を行うようになりました。  
ブラウザから``localhost:9000``にアクセスしてみてください。