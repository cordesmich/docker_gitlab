Testsystem / kein automatischer Neustart (--restart always \)
----

Docker install 
	https://store.docker.com/editions/community/docker-ce-server-ubuntu?tab=description

----

Erster Start:
	sudo docker run --detach \
	    --hostname gitlab.example.com \
	    --publish 443:443 --publish 80:80 --publish 22:22 \
	    --name gitlab \
	    --volume /srv/gitlab/config:/etc/gitlab \
	    --volume /srv/gitlab/logs:/var/log/gitlab \
	    --volume /srv/gitlab/data:/var/opt/gitlab \
	    gitlab/gitlab-ce:latest

----

Neu Starten / Nach PC neustart
	sudo docker restart gitlab

----

Update GITLAB

To upgrade GitLab to a new version you have to:
Stop the running container:
	sudo docker stop gitlab

Remove existing container:
	sudo docker rm gitlab

Pull the new image:
	sudo docker pull gitlab/gitlab-ce:latest

Create the container once again with previously specified options:

	sudo docker run --detach \
	    --hostname gitlab.example.com \
	    --publish 443:443 --publish 80:80 --publish 22:22 \
	    --name gitlab \
	    --volume /srv/gitlab/config:/etc/gitlab \
	    --volume /srv/gitlab/logs:/var/log/gitlab \
	    --volume /srv/gitlab/data:/var/opt/gitlab \
	    gitlab/gitlab-ce:latest
----

Backup
	sudo docker exec -t gitlab gitlab-rake gitlab:backup:create
Zeige Backups:
	sudo ls -l /srv/gitlab/data/backups/ 
Copy Backup:
	sudo cp /srv/gitlab/data/backups/1493985556_2017_05_05_gitlab_backup.tar /home/cord778/docker\ readme/1493985556_2017_05_05_gitlab_backup.tar



----------------------------------


sudo docker run --detach \
	--hostname gitlab.example.com \
	--publish 443:443 --publish 80:80 --publish 22:22 \
	--name gitlab \
	--restart always \
	--volume /srv/gitlab/config:/etc/gitlab \
	--volume /srv/gitlab/logs:/var/log/gitlab \
	--volume /srv/gitlab/data:/var/opt/gitlab \
	gitlab/gitlab-ce:latest

sudo docker run --detach \
--hostname gitlab.example.com \
--publish 443:443 --publish 80:80 --publish 22:22 \
--name gitlab \
--volume /srv/gitlab/config:/etc/gitlab \
--volume /srv/gitlab/logs:/var/log/gitlab \
--volume /srv/gitlab/data:/var/opt/gitlab \
gitlab/gitlab-ce:latest


