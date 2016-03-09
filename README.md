# factorio
Factorio headless server on Docker


## Quick start

### Docker volumes

* Create the volume container, i.e. `export FACTORIO_DATA=factorio-data`

```
docker run --name ${FACTORIO_DATA} -v /opt/factorio/saves busybox
```

* Create a new save

```
docker run --rm -it --volumes-from=$FACTORIO_DATA wnkz/factorio /opt/factorio/bin/x64/factorio --create mygame
```

* Run the server

```
docker run -d --name factorio --restart=always -p 34197:34197/udp --volumes-from=$FACTORIO_DATA wnkz/factorio /opt/factorio/bin/x64/factorio --start-server mygame
```

### Local volume mount (easier when you have existing saves)

* Copy your save to a directory on your server, i.e. `~/factorio_saves/mygame.zip`

* Run the server

```
docker run -d --name factorio --restart=always -p 34197:34197/udp -v ~/factorio_saves:/opt/factorio/saves wnkz/factorio /opt/factorio/bin/x64/factorio --start-server mygame
```
