##cssを圧縮してみる  

cssを圧縮することができる、grunt-contrib-cssminを使ってみましょう。

手順
  1. grunt-contrib-cssminをインストール
  1. 圧縮するcssファイルと圧縮後のファイルを指定

###1.grunt-contrib-cssminをインストール

まずnpmでgrunt-contrib-cssminをインストールしてみましょう。  

```
$ npm install grunt-contrib-cssmin --save-dev
```

これでcssminの導入は完了です。おなじみの手順ですね。  

###2.圧縮するcssファイルと圧縮後のファイルを指定

```
module.exports = function(grunt){
 
  pkg: grunt.file.readJSON('package.json'),  //package.jsonを取得
 
  grunt.initConfig({      //grunt.initConfigの中にタスクの設定を記述する
    cssmin: {
      hoge: { //hogeの名前は任意です
        src: ['css/sample01.css', 'css/sample02.css'], //配列で圧縮したいファイルを指定
        dest: 'css/sample.min.css'  //圧縮したファイルをcssフォルダの中にsample.min.cssという名前で生成
      }
    },
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
  grunt.loadNpmTasks('grunt-contrib-cssmin');
 
  //defaultと設定することで、登録しているタスクを実行する。
  grunt.registerTask('default', ['connect', 'watch']);
 
};
```

あとはコマンドラインから``grunt cssmin``を実行してあげるだけです。  
圧縮するファイルの指定方法は上記で説明した方法以外にもあります。  
詳しい使い方は是非調べてみてください。  

以上です。  


次はjavascriptを結合する、grunt-contrib-concatの使用方法です。  

[javascriptを結合してみる](https://github.com/kaiji0811/studying_grunt/wiki/Live-Reload%E3%82%92%E4%BD%BF%E3%81%A3%E3%81%A6%E3%81%BF%E3%82%8B)