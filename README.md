This app has been deployed directly from the prebuilt image.

1. docker pull syncthing/syncthing:1.9.0
2. docker tag syncthing/syncthing:1.9.0 dokku/syncthing:1.9.0
3. dokku tags:deploy syncthing 1.9.0
3. dokku storage:mount syncthing /var/lib/dokku/data/storage/syncthing:/var/syncthing
4. dokku proxy:ports-add syncthing http:80:8384 http:22000:22000
5. dokku config:set --no-restart syncthing DOKKU_LETSENCRYPT_EMAIL=<my-email>
6. dokku letsencrypt syncthing
7. dokku letsencrypt:cron-job --add
