##Live Reloadを使ってみる  

watchで監視しているファイルに変更があった時に、自動的にブラウザを更新するとても便利な機能、  
Live Reloadを使ってみましょう。  
※google chromeを使用し説明します。

手順
  1. ブラウザにアドオンをインストール
  1. watchのオプションでlivereloadをtrueにする

###1.ブラウザにアドオンをインストール
Live Reloadを使用するためには、ブラウザ側にアドオンを導入する必要があります。  

[Live Reload - Google Chrome](https://chrome.google.com/webstore/detail/livereload/jnihajbhpnppcggbcgedagnkighmdlei)  

これでブラウザ側の設定は終わりました。簡単ですね。  

###2.watchのオプションでlivereloadをtrueにする  

監視ファイルに変更があった際にブラウザを更新するので、  
Gruntfile.jsで設定したwatchのオプションでlivereloadをtrueにしてあげましょう。  
コードを見てみます。

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
      html: {
          options: {
              livereload: true // live reloadの機能をオンにする。
          },
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
これでLive Reloadが利用可能になりました。  
後はブラウザ側のアドオンのアイコンをぽちっと押してあげるだけです。  

次は指定したcssを圧縮する、grunt-contrib-cssminの使用方法です。  

[cssを圧縮してみる](https://github.com/kaiji0811/studying_grunt/wiki/css%E3%82%92%E5%9C%A7%E7%B8%AE%E3%81%97%E3%81%A6%E3%81%BF%E3%82%8B)