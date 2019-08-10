docker iamgeのbuild
```
docker build --tag webapp .
```

docker container起動
```
docker run -d -p 443:443 -p 80:80 webapp
```

証明書作成の流れ
```
2048ビットの秘密鍵作成
openssl genrsa 2048 > server.key

CSRを作成
openssl req -new -key server.key > server.csr

CSRから自己署名証明書を作成
openssl x509 -in server.csr -days 100 -req -signkey server.key > server.crt
```