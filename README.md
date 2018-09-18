# distributed-http-server

## Front End
```
python3 -m front_end_server 127.0.0.1 5000 127.0.0.1 5001 1
```

## Dockerize Front End
```
sudo docker build -f front_end_server/Dockerfile -t distribute-http-server-fe:latest .
sudo docker run -p 5000:5000 -p 5001:5001 distribute-http-server-fe
```

## Back End
```
python3 -m back_end_server 127.0.0.1 5001 0
```

## Dockerize Back End
```
sudo docker build -f back_end_server/Dockerfile -t distribute-http-server-be:latest .
sudo docker run -p 5001:5000 distribute-http-server-be
```

## cURL Examples
```
curl -X GET http://0.0.0.0:5001
curl -X POST http://0.0.0.0:5000 -d '{"key1":"value1", "key2":"value2"}'
```
