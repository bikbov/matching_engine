🦀 Demo: https://alicebob.ru/

Price-Time Priority algorithm

## Build ##
```
docker build -t matching_be .
docker save -o matching_be.tar matching_be
gzip matching_be.tar
scp -P 56929 matching_be.tar.gz root@aeserver:.
rm matching_be.tar.gz
```

## Deploy ##
```
ssh root@aeserver -p 56929
docker stop matching_be
docker rmi matching_be
gunzip matching_be.tar.gz
docker load -i matching_be.tar
rm matching_be.tar
docker run --rm -d --network exch --name matching_be matching_be
```
