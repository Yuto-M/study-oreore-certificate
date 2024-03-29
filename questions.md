- ~~SSL化の流れ・仕組み~~
  - 秘密鍵作成→CSR作成→CSRを登録して証明書発行(オレオレだとここが自分で署名することになる)
  - 仕組みは下記サクラ参照。最終的には共通鍵でやり合う。
    - https://ssl.sakura.ad.jp/column/ssl/
    - 共通鍵説明 https://wa3.i-3-i.info/word1839.html
- ~~オレオレ証明書の仕組み~~
  - SSL通信の暗号化をしたりして通信を安全にしてくれる仕組み。web的にはwebサーバーとwebブラウザの間の通信を安全にしてくれる仕組み。
  - CA: webサーバーが本物であることを証明してくれる機関。
  - 本来CAに自分のwebサイトを登録して自分のwebサイトが本物であることを証明して、証明書をCAからもらう。その証明書をクライアントに返し、クライアントはブラウザに登録されているCAの情報を元にサーバーを信用するっていうのがSSL化の流れ。
  オレオレ証明書とは、CAに登録せずに、自分で証明書を作成してその証明書を用いてSSL化することをいう。なんでこんなんするかっていうと証明書（サーバー証明書っていう）をCAから発行してもらうには有料で手続きがあり開発中はめんどくさいため。

- ~~nginx.confの設定内容~~
  - ssl_protocolはTLSを指定しておくのが鉄板。下記参照。
  - https://gist.github.com/koudaiii/735ef14b83ee31ac0967
  - ssl周りの設定説明下記参照。
  - https://cspssl.jp/support/nginx/config.php
  - aliasの説明下記参照。
  - https://heartbeats.jp/hbblog/2012/04/nginx05.html
- ~~opensslコマンドで作るファイルの意味~~
- ~~`chmod 755 -R /var`って`chmod -R 755 /var`じゃだめなんかな？~~
- ~~Dockerfileの`EXPOSE 443`~~
  - コンテナのポート公開。ポートフォワーディングは別途必要。 https://qiita.com/soushiy/items/0945bcbc7ecce4822985
- ~~Dockerfileの`CMD`のとこ~~
  - nginxをforegroundで動かしてる。下記参照。
  - https://heartbeats.jp/hbblog/2014/07/3-tips-for-nginx-on-docker.html
- ~~`docker build --tag webapp .`このコマンドの意味。~~
  - imageを`webapp`っていうタグ名で作成。