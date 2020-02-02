## docker-rclone-mount

	version: '3'
	services:
	  rclone-ovh:
	    image: pknw1/rclone-mount
	    container_name: rclone-mount
	    security_opt:
	      - apparmor:unconfined
	    cap_add:
	      - SYS_ADMIN
	    devices:
	      - "/dev/fuse:/dev/fuse"
	    environment:
	      - PUID=666
	      - PGID=666
	      - PUMASK=0000
	      - TZ=Europe/London
	      - RCLONE_REMOTE_MOUNT=remote:/
	    volumes:
	      - ./config/rclone-mount:/config
	      - /mnt/rclone-remote:/data:shared
	      - /tmp:/tmp
	      - /etc/localtime:/etc/localtime
	    restart: unless-stopped
