# webroom
Remoのようなバーチャル空間の作成

## 立ち上げ方

```
docker-compose up -d
```

## URL

http://localhost:8080

## 内容

- 3D空間上にアバターが出現しRoomの中でWeb会議ができる

## 構成

| サーバー名       | 名称 | ポート番号 |
|:-----|:-------------------------------|:-----|
| Front開発サーバー(React)    | front | 8080 |
| APIサーバー(FastAPI)    | back | 8001 |
| Websocketサーバー(FastAPI)    | socket | 3001 |
| Webサーバー(nginx)    | web | 8000 |
| DBサーバー(MySQL)    | db | 3336 |