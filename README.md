# Send webcam feed to Twitch using Restreamer on Raspberry Pi

Example [Docker Compose](https://www.baeldung.com/ops/docker-compose) config for [Tutorial: Broadcast webcam to Twitch using Raspberry Pi and Datarhei Restreamer](https://rightsaidjames.com/2023/05/stream-webcam-twitch-raspberry-pi-datarhei-restreamer/), generated using [Composerize](https://www.composerize.com/). The setup defined in `docker run` has been modified to create `config` and `data` [bind mounts](https://docs.docker.com/storage/bind-mounts/) in the directory where the `docker compose` command is run from.

To use, create a new directory (e.g. restreamer) and navigate to it, pull down this `docker-compose.yml` file using [wget](https://www.digitalocean.com/community/tutorials/how-to-use-wget-to-download-files-and-interact-with-rest-apis), then run `docker compose up -d`.

Follow Docker's [post-install steps for Linux](https://docs.docker.com/engine/install/linux-postinstall/) to ensure that Docker (and the Restreamer container) start automatically after the Pi is turned on. When restarted, the Restreamer app should recreate its last state, so if you turned off your Pi while connected to Twitch then Restreamer will re-connect to Twitch after it has been restarted.

To stop your container temporarily, run `docker compose stop`. To decommission the app, run `docker compose down`. The bind mounts created during the `up` command will remain, and can be reused if you recreate the app in future, but also can be removed simply by deleting the folders from your Pi's filesystem.
