# docker-syncthing-inotify

Example startup with persistent storage on /home/syncthing, mounted from
the host folder /var/lib/syncthing:

```
export SYNCTHING_USER="host-user"
export SYNCTHING_GROUP="host-group"
export SYNCTHING_DIR="/var/lib/syncthing"
sudo mkdir "${SYNCTHING_DIR}"
sudo chown "${SYNCTHING_USER}":"${SYNCTHING_GROUP}" "${SYNCTHING_DIR}"

sudo docker run \
  --link=syncthing
  --name=syncthing-inotify \
  --user=$(id -u ${SYNCTHING_USER}):$(id -u ${SYNCTHING_GROUP}) \
  --detach=true \
  --restart=always \
  --volume="${SYNCTHING_DIR}":"/home/syncthing" \
  providernl/syncthing-inotify
```
