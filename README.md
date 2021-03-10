This app is deployed with a Dockerfile pointing at the official Dockerfile.

1. dokku storage:mount syncthing /var/lib/dokku/data/storage/syncthing:/var/syncthing
1. dokku proxy:ports-add syncthing http:80:8384 http:22000:22000
1. dokku config:set --no-restart syncthing DOKKU_LETSENCRYPT_EMAIL=<my-email>
1. dokku letsencrypt syncthing
1. dokku letsencrypt:cron-job --add
1. git remote add dokku dokku@dokku.youngram.com:syncthing
1. git push dokku main
