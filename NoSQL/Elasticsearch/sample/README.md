# Elasticsearchサンプルコード

## インストール
```bash
docker pull elasticsearch:6.6.1
```

インストールしたかの確認
```bash
docker image ls
```

## 起動
```bash
docker network create elasticnetwork
```

```bash
docker run -d --name elasticsearch --net elasticnetwork -p 9200:9200 -p 9300:9300 -e "discovery.type=single-node" elasticsearch:6.6.1
```

```bash
curl -XGET http://localhost:9200/
```

## 複数のノードを起動
```bash
docker run -d --name elasticsearch --net elasticnetwork -p 9200:9200 -p 9300:9300 -e "discovery.type=single-node" -e "node.max_local_storage_nodes=2" elasticsearch:6.6.1
```