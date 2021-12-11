Just a learning project.

```
go get -u github.com/praveen001/go-rtmp-web-server
```

# RTMP Restreaming Server

Restreaming server that can stream to Youtube, Twitch and Custom RTMP servers. Similar to [restream.io](https://restream.io)

- [Development setup](#start-server-for-development)
- [Production setup](#start-server-in-production-mode)

![Screenshot](https://raw.githubusercontent.com/praveen001/go-rtmp-web-server/master/screenshot.png)

# Start server for development

It consists of three components - a web server, RTMP restreaming server and frontend. You have to start them individually.

It uses a .env file from ./scripts/dev.env for all the configurations

**Clone the project**
go get -u github.com/praveen001/go-rtmp-web-server

**Dependencies**
- node
- yarn
- ffmpeg 4.x
- go 1.11.x
- docker
- docker-compose
- mysql
- redis

**Start web server**

```
set -o allexport
[[ -f ./scripts/dev.env ]] && source ./scripts/dev.env
set +o allexport
go run main.go web
```

**Start RTMP server**

```
set -o allexport
[[ -f ./scripts/dev.env ]] && source ./scripts/dev.env
set +o allexport
go run main.go rtmp
```

**Start frontend**

```
cd frontend
yarn
yarn start
```

# Start server in production mode

All the components are wrapped in docker. Just run docker compose.

It uses a .env file from ./scripts/prod.env for all the configurations.

```
docker-compose up
```
