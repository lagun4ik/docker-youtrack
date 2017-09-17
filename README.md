# 📈 YouTrack on Docker
	
This repository contains a Docker image of JetBrains [YouTrack](http://www.jetbrains.com/youtrack).

* The Docker image is available at [lagun4k/youtrack](https://registry.hub.docker.com/u/lagun4ik/youtrack)
* The GitHub repository is available at [lagun4k/docker-youtrack](https://github.com/lagun4ik/docker-youtrackr)

## Usage with docker-compose

See [docker-compose.yml](https://github.com/lagun4ik/docker-youtrack/blob/master/docker-compose.yml) for example

## Usage

Create a named container 'youtrack'.

```bash
docker create --name youtrack lagun4k/youtrack
```

Start the container.

```bash
docker start youtrack
```

### Additional settings

YouTrack stores its data and backups at ```/opt/youtrack/data/``` and ```/opt/youtrack/backup/``` in the container.
If you wish to re-use data, it is a good idea to set up a volume mapping for these two paths. 
You can use `Xms` and `Xmx` environment variables for tuning jre.

For example:

```bash
docker run -t \
 --name="youtrack" \
 -v /data/youtrack/data/:/opt/youtrack/data/ \
 -v /data/youtrack/backup/:/opt/youtrack/backup/ \
 -e "Xms=512m" \
 -e "Xmx=1g" \
 -p 80:80 \
 lagun4k/youtrack
```