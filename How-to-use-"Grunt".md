#JavaScript製タスクランナー　Gruntを使ってみよう！

>
今回のノートではMacでの導入方法を説明します。  
Windowsの方はググって下さい！沢山ググって下さい！基本的なフローは同じです。

###Gruntってなに？
>
GruntはNode.jsを使ったJavaScript製のタスクランナーです。  
決まった動作をおこなったときに、あらかじめ設定したタスクを実行してくれます。  
Gruntを利用するためには**Node.js**が必要です。

##Node.jsって？
>
詳しくは割愛しますが、一言で説明するとサーバーサイドで使えるJavaScriptです。  
GruntもこのNode.jsがなければ動きません。  
まずはNode.jsをインストールしてみましょう。

##Node.js インストール手順
>
1. nvmをインストール
1. Node.jsをインストール
1. バージョンを変更する

###nvmをインストール
>
nvmとは、Node Version Managerの略称で、Node.jsのバージョンを管理するシステムのことです。  
nvmを導入することで、簡単にNode.jsのバージョンを変更することが出来ます。

nvmをインストールするには以下のコマンドをターミナルから実行して下さい。  
※nvmをインストールするにはgitが導入されていることが前提となります。

+ ***ホームディレクトリにnvmをインストール***
```
$ git clone git://github.com/creationix/nvm.git ~/.nvm
```

