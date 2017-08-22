# YouTrack on Docker

This repository contains a Docker image of JetBrains [YouTrack](http://www.jetbrains.com/youtrack).

Versions included:
* YouTrack 2017.3
* Based on YouTrack 6.5.16953 (December, 10 2015)

# Build

* build YouTrack 2017.3
```
docker build -t my-youtrack github.com/maxivak/docker-youtrack.git#master:2017.3
```


* build YouTrack 6.5
```
docker build -t my-youtrack github.com/maxivak/docker-youtrack.git#master:6.5
```


# Run


* create data volumes

```bash
sudo docker volume create --name youtrack-data
sudo docker volume create --name youtrack-backup
```

* run container

```
sudo docker run -d \
 --name="youtrack" \
 -v youtrack-data:/opt/youtrack/data/ \
 -v youtrack-backup:/opt/youtrack/backup/ \
 -p 10081:80 \
 my-youtrack
```

* Youtrack listens on port 80 in the container and it will map to port 10081 on the host.


## Settings

YouTrack stores its data and backups at ```/opt/youtrack/data/``` and ```/opt/youtrack/backup/``` in the container. If you wish to re-use data, it is a good idea to set up a volume mapping for these two paths. For example:
