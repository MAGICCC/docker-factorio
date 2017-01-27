# Factorio Docker image

This image includes the headless build of Factorio with paths set to store data in the /data folder and configuration in the /config folder which can both be used as volumes.

## Starting a server

### Creating the savefile

Before first start up you should make sure to create a save file for the server to load by running:

    docker run --rm \
        -v /path/to/data:/data \
        -v /path/to/config:/config \
        /opt/factorio/bin/x64/factorio --create /data/saves/my-save.zip

After that you can use the givena volumes for running the server, for example using Docker Compose!

### Example Docker Compose file

```yaml
version: "2"

services:
    factorio:
        # The image to use, version number of the server can be used as a tag.
        image: icedream/factorio:0.14.2

        # Volumes to mount in
        volumes:
            - /path/to/data:/data
            - /path/to/config:/config

        # Optionally replace the command to run to configure further details
        # or even make use of map generation or server settings files.
        #command: /opt/factorio/bin/x64/factorio --start-server-load-latest --rcon-password somepassword
```