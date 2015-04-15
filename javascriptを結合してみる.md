##javascriptを結合してみる  

今回は複数のファイルを任意に結合することができる、grunt-contrib-concatを使って、javascriptファイルを結合してみましょう。

手順
  1. grunt-contrib-concatをインストール
  1. 結合するファイルを指定

###1.grunt-contrib-concatをインストール

おなじみnpmでインストールです。  

```
$ npm install grunt-contrib-concat --save-dev
```

###2.結合するファイルを指定

今回はjsフォルダ配下にあるjsファイルを全て結合します。  
ソースを見てみましょう。

```
module.exports = function(grunt){
 
  pkg: grunt.file.readJSON('package.json'),
 
  grunt.initConfig({
    cssmin: {
      hoge: {
        src: ['css/sample01.css', 'css/sample02.css'],
        dest: 'css/sample.min.css'
      }
    },
    concat: {
      files: {
        src : 'js/*.js', // ファイル名の部分を＊にすることで拡張子がjsの全てのファイルを指定できる
        // 出力ファイルの名前・パス指定
        dest: 'js/common.js' // 結合したファイルをcommon.jsという名前で生成
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
  grunt.loadNpmTasks('grunt-contrib-concat');
 
  //defaultと設定することで、登録しているタスクを実行する。
  grunt.registerTask('default', ['connect', 'watch']);
 
};
```

基本的な使い方はほとんどcssminの時と同じですね。  

以上です。  


次はjavascriptを圧縮する、grunt-contrib-uglifyの使用方法です。  

[javascriptを圧縮してみる]()