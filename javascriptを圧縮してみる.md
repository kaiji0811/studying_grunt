##javascriptを圧縮してみる  

前回結合したjavascriptを圧縮してみましょう。  
使用するプラグインはgrut-contrib-uglifyです。

手順
  1. grunt-contrib-uglifyをインストール
  1. 圧縮するファイルを指定

###1.grunt-contrib-uglifyをインストール

npmでインストールです。もう覚えましたか？  

```
$ npm install grunt-contrib-uglify --save-dev
```

###2.圧縮するファイルを指定

前回結合したcommon.jsを圧縮してみましょう。

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
        src : 'js/*.js',
        dest: 'js/common.js'
      }
    },
    uglify: {
      dist: {
        files: {
          'js/common.min.js': 'js/common.js'
        }
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
  grunt.loadNpmTasks('grunt-contrib-uglify');
 
  //defaultと設定することで、登録しているタスクを実行する。
  grunt.registerTask('default', ['connect', 'watch']);
 
};
```

jsフォルダ配下にcommon.min.jsが生成されていると思います。  

また、プラグインにはオプションが設定できるものもあります。  
いくつかオプションを紹介します。  

* mangle -> ローカル変数の名前を短くし難読化します。trueでオン。
* compress -> 冗長なコードを短くまとめてくれます。trueでオン。
* beautify -> 改行やインデントは取り除かず、そのまま見やすく整形します。
* report -> 'gzip'を指定することでgzip化してくれます。
* preserveComments -> コメントの残し方を指定します。
  - 'all' -> 全てのコメントを残します。
  - 'some' -> /*! から始まるコメントだけ残ります。

grunt-contrib-uglifyのオプション指定方法を見ていきます。

```
uglify: {
  options: { // uglifyオブジェクトの中でオプションを定義
    mangle: true,
    conpress: true,
    preserveComments: 'some'
  },
  dist: {
    files: {
      'js/common.min.js': 'js/common.js'
    }
  }
},
```

uglifyの中でoptionsを定義しているだけですね。  
以上です。  


次はjavascriptの構文チェックをしてくれる、jshintの使い方です。  

[javascriptを圧縮してみる](https://github.com/kaiji0811/studying_grunt/wiki/javascript%E3%82%92%E5%9C%A7%E7%B8%AE%E3%81%97%E3%81%A6%E3%81%BF%E3%82%8B)