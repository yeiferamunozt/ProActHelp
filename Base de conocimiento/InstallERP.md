Todos los dominio estan bajo el hospedaje en latinoamerican hosting
Los dominio estan alojados en conexcol


Domain: culturac.com

## Admin access

```bash
git clone -c core.sshCommand="ssh -i ~/.ssh/picurit_bitbucket" git@bitbucket.org:picurit/erp_col
git config core.sshCommand "ssh -i ~/.ssh/picurit_bitbucket"
```


# Install Test Environment

## Prerequisites

- [Docker](https://docs.docker.com/install/)
- [Docker Compose](https://docs.docker.com/compose/install/)
- [Git](https://git-scm.com/downloads)

## Create configuration files

```bash
mkdir -p ~/erp/config
touch ~/erp/config/.env
echo 'source $HOME/erp/config/.env' >> ~/.bashrc
mkdir -p ~/docker
```

## Save your access tokens in an environment variable

```bash
#echo "export NC_AT=<your_access_token>" >> ~/erp/config/.env
echo "export NC_AT=ATCTT3xFfGN0zzqBDN_Ha-ghBfjCsQiB85ioqpVVdJPlHKkVHRuODPVT347gaTgxoyCT-dvscG0mtDtf6MabGgKWmMhLsLVXXVszaPfr2zTRkv1wa7_Rn0HS-UZnwX24T9l_p7BbO8qvCB03rYBV6spPuQPK3L5uXhdn-8f26xYD4sNpwzj7iHY=D5E7BAF3" >> ~/erp/config/.env
source ~/.bashrc
```

## Bootstrap Containers for test environment

Clone nestcolony repository

```bash
cd ~/docker
git clone https://x-token-auth:${NC_AT}@bitbucket.org/picurit/nestcolony.git
```

Add the NESTCOLONY_PATH variable to the .env file

```bash
echo 'export NESTCOLONY_PATH=$HOME/docker/nestcolony' >> ~/erp/config/.env
source ~/.bashrc
```

Change to the nestcolony directory

```bash
cd $NESTCOLONY_PATH
```

Copy example devcontainer config from `devcontainer-example` to `.devcontainer`
    
```bash
cp -R devcontainer-example .devcontainer
```

## Change the default password

```bash
sed -i 's/MYSQL_ROOT_PASSWORD: 123/MYSQL_ROOT_PASSWORD: 3rpt00rt3st/g' $NESTCOLONY_PATH/.devcontainer/docker-compose.yml
```

## Manually start containers

Start the containers in the background

```bash
#docker compose -f $NESTCOLONY_PATH/.devcontainer/docker-compose.yml up -d
docker compose \
-f $NESTCOLONY_PATH/.devcontainer/docker-compose.yml \
up -d
```

## Manually stop containers

```bash
docker compose \
-f $NESTCOLONY_PATH/.devcontainer/docker-compose.yml \
down -v
```

Ensure that frappe user has the same uid and gid as the host user

> It may take a while to complete ~10 minutes

```bash
docker compose \
--project-name devcontainer \
-f $NESTCOLONY_PATH/.devcontainer/docker-compose.yml \
exec \
--user root \
frappe \
bash -c "find / -user frappe -exec chown -v -h $(id -u) '{}' \; || true && find / -group frappe -exec chgrp -v $(id -g) '{}' \; || true && groupmod -g $(id -g) frappe || true && usermod -u $(id -u) -g $(id -g) frappe"
```

Enter the interactive shell for the development container with the following command

```bash
#docker exec -e "TERM=xterm-256color" -w /workspace/development -it devcontainer-frappe-1 bash
docker compose \
--project-name devcontainer \
-f $NESTCOLONY_PATH/.devcontainer/docker-compose.yml \
exec -e "TERM=xterm-color" \
 -w /workspace/development \
 -it frappe bash
```

# Setup bench

Create a new bench

```bash
bench init --skip-redis-config-generation --frappe-branch version-14 --frappe-path https://x-token-auth:ATCTT3xFfGN0um5nEQTHIS3YZVRy-mwI9qGdf2Y_pYBdmaD1xs-fdxBNWKtJz230ydfEvejRIAqo9M-O2836L0ppWmnIT3gAGlD7DZrVaI39UXjupJiz0gn6M9ml6uerRUPP3YmLPd4d9h58kNZWZ_5zu4Q1VOKAsG4vwHGhBtWj0vVMl3wAFmI=79CA1A62@bitbucket.org/picurit/frappe frappe-bench
cd frappe-bench
```

## Setup hosts

We need to tell bench to use the right containers instead of localhost. Run the following commands inside the container:

```bash
bench set-config -g db_host mariadb
bench set-config -g redis_cache redis://redis-cache:6379
bench set-config -g redis_queue redis://redis-queue:6379
bench set-config -g redis_socketio redis://redis-socketio:6379
```

## Install apps

bench get-app --branch version-14 --resolve-deps payments
bench get-app --branch version-14 --resolve-deps https://x-token-auth:ATCTT3xFfGN0OvZ3q_uYSKaUKIA2_o_jZzsq1tyqP9g0y9y4IiqArMKalHObyGEFUNmVLJAmiMeEWGSIBVWDUTX3TuuOAVqo5K945-faypyan4Bfpz8KhCN4v6Kl9JPowsK5ogOLkMeFVhyKv4kSb1U4ki4KMdNR2sK5FQWbtXhJo4tOM-OYjck=EF989A7F@bitbucket.org/picurit/erpnext
bench get-app --branch version-14 hrms
bench get-app --branch develop education
bench get-app --branch version-14 --resolve-deps https://x-token-auth:ATCTT3xFfGN0kGCK-fwWr5Qv3amdr_QgMeYfIZL25ECJQm5HMpWAjtSCmLjkwdytzICUCx7LnmdISVXIpnhTdw4lAvG2QKdioXji9udljPOV9zTV4ao_IlTnSVXYfqg5JctOgf7x4VyzjLLG3Ts5wt6758k9kh5Vb7y58zx6C-7oWaErmO21ygQ=095626AE@bitbucket.org/picurit/whitelabel
bench get-app --branch version-14 https://x-token-auth:ATCTT3xFfGN0UYjB2nuFsqdQJoObLx90FckYSLk6wAX-tkO_-agK1Sdh5Gqpslz-USe1lbVHmW7vEodnPl9xIDjBVr9BwQvAd08gHJcRvuvLGCrsdo_P8p1W_kaFiV9v3AEj_Wu6z5cWJhosNIPXfGvy5b7u0kQ9sXxaZ3Vg0wFTAUWSYcS_QoI=5B9DC1F5@bitbucket.org/picurit/erp_improve


bench get-app --branch v1 https://x-token-auth:ATCTT3xFfGN0JoKz9rWWqGFd8T8PbV3T9UiyITBnX_qiBNjiqOESHkt9wXW36mCDqejve0tP_JKAQEjGvUz2NakPbIJKAWRB6cnQ2WVKHCFphMlZ9Fc-89uSHM8E5aaNP69PDi_a38Nrrfu_nmC2V0eLYiojC0lubX7ID9-CVzFmqcxylXXQOyc=A4F8AEF2@bitbucket.org/picurit/frappe_better_attach_control
bench get-app --branch version-14 https://x-token-auth:ATCTT3xFfGN0gkog_keqL26-XqkpVHgxALGUjtdzFopFc0Tv--sY6wLmLAf8np7ZzA9GyKlA-CXynWDTmg8k8eGi_NjR_0mK6UaIDMLcx8XZDjpA4wy9KXCnEGGW1fGciXruNCMWUsuuLjvVvpxHxNqUS2QWRzuLgj3MTcnWKIpVYCP3u89JZNQ=C564AD23@bitbucket.org/picurit/erp_col




## Create a new site with bench

```bash
bench new-site test.boomb.com.co \
 --db-name test.boomb.com.co \
 --mariadb-root-password '3rpt00rt3st' \
 --admin-password 'sys4dm!nt3st' \
 --no-mariadb-socket \
 --install-app payments \
 --install-app erpnext \
 --install-app hrms \
 --install-app education \
 --install-app whitelabel
```

Remove site forced

```bash
bench drop-site test.boomb.com.co --force
```

## Disable developer mode (Default)

```bash
bench --site atta.local set-config developer_mode 0
bench --site atta.local clear-cache
```

## Enable developer mode (If you want to customize)

```bash
bench --site atta.local set-config developer_mode 1
bench --site atta.local clear-cache
```

## Start instance

```bash
bench start
```

## Create backup

```bash
bench --site culturac.picurit.com backup --with-files --compress
```

## Restore backup

```bash
bench --site test.boomb.com.co \
 restore test.boomb.com.co/private/backups/doc-recreate-test_boomb_com_co-database.sql.gz \
 --with-public-files test.boomb.com.co/private/backups/doc-recreate-test_boomb_com_co-files.tar \
 --with-private-files test.boomb.com.co/private/backups/doc-recreate-test_boomb_com_co-private-files.tar \
 --mariadb-root-password '3rpt00rt3st'

bench --site test.boomb.com.co \
 restore test.boomb.com.co/private/backups/doc-recreate-test_boomb_com_co-database.sql.gz \
 --mariadb-root-password '3rpt00rt3st'
```

20231011_203134-culturac_picurit_com

bench --site dev-culturac.picurit.com \
  restore dev-culturac.picurit.com/private/backups/20231011_203134-culturac_picurit_com-database.sql.gz \
  --with-public-files dev-culturac.picurit.com/private/backups/20231011_203134-culturac_picurit_com-files.tgz \
  --with-private-files dev-culturac.picurit.com/private/backups/20231011_203134-culturac_picurit_com-private-files.tgz \
  --mariadb-root-password '3rplucky.pr0d'

## Migrate site

```bash
bench --site dev-culturac.picurit.com migrate
```

## Install healthcare app

```bash
bench --site dev-culturac.picurit.com install-app healthcare
```

## Access to the database container

```bash
cd $NESTCOLONY_PATH
docker compose \
--project-name nestcolony_devcontainer \
-f .devcontainer/docker-compose.yml \
exec -e "TERM=xterm-256color" \
 -w /var/lib/mysql \
 -it mariadb bash
```








# Install Production Environment

## Prerequisites

- [Docker](https://docs.docker.com/install/)
- [Docker Compose](https://docs.docker.com/compose/install/)
- [Git](https://git-scm.com/downloads)

## Create configuration files

```bash
mkdir -p ~/erp/config
touch ~/erp/config/.env
echo 'source $HOME/erp/config/.env' >> ~/.bashrc
mkdir -p ~/docker
```

## Save your access tokens in an environment variable

```bash
#echo "export NC_AT=<your_access_token>" >> ~/erp/config/.env
echo "export NC_AT=ATCTT3xFfGN0zzqBDN_Ha-ghBfjCsQiB85ioqpVVdJPlHKkVHRuODPVT347gaTgxoyCT-dvscG0mtDtf6MabGgKWmMhLsLVXXVszaPfr2zTRkv1wa7_Rn0HS-UZnwX24T9l_p7BbO8qvCB03rYBV6spPuQPK3L5uXhdn-8f26xYD4sNpwzj7iHY=D5E7BAF3" >> ~/erp/config/.env
echo "export EB_AT=ATCTT3xFfGN0kiUuIIFwGF6xha3BMBO1wmiPTgHe_oJ7OzGVlq7wdwH3gu7rEgJdGLw5CplV9a-uWmLPRMxI7lovf5k8m5UuxrpIZqmwVpUuthn4bkOTTU6Lf-9vRCQbWcYNKmPW3Q5jaL6m4o0f4G__A7-ADtZgIzhgYSryqIiG2aerFVH8HRM=6C988B94" >> ~/erp/config/.env
source ~/.bashrc
```

## Clone the nestcolony repository

```bash
cd ~/docker
git clone https://x-token-auth:${NC_AT}@bitbucket.org/picurit/nestcolony.git
```

Add the NESTCOLONY_PATH variable to the .env file

```bash
echo 'export NESTCOLONY_PATH=$HOME/docker/nestcolony' >> ~/erp/config/.env
source ~/.bashrc
```

## Clone the erpbuilder repository

```bash
cd ~/docker
git clone https://x-token-auth:${EB_AT}@bitbucket.org/picurit/erpbuilder.git
```

Add the BUILDER_PATH variable to the .env file

```bash
echo 'export BUILDER_PATH=$HOME/docker/erpbuilder' >> ~/erp/config/.env
source ~/.bashrc
```

## Set up builder environment

```bash
cd $BUILDER_PATH
cp defaults/* .
```

## Build the ERP image

```bash
cd $NESTCOLONY_PATH

source $BUILDER_PATH/var $BUILDER_PATH
export FRAPPE_PATH INSTANCE_BRANCH APPS_JSON_BASE64 CUSTOM_IMAGE CUSTOM_TAG
docker build \
  --platform=$(docker buildx inspect | awk -F'[ ,]' '/Platform/{print $2}') \
  --build-arg=FRAPPE_PATH=$FRAPPE_PATH \
  --build-arg=FRAPPE_BRANCH=$INSTANCE_BRANCH \
  --build-arg=APPS_JSON_BASE64=$APPS_JSON_BASE64 \
  --tag=$CUSTOM_IMAGE:$CUSTOM_TAG \
  --file=images/custom/Containerfile . && docker image prune -f
```

## Setup Environment Variables 

```bash
cp example.env .env
```

Change the DB_PASSWORD in the .env file

```bash
sed -i 's/DB_PASSWORD=.*/DB_PASSWORD=3rplucky.pr0d/' .env
```

Change LETSENCRYPT_EMAIL variable for your email

```bash
sed -i 's/LETSENCRYPT_EMAIL=.*/LETSENCRYPT_EMAIL=manager.picurit@gmail.com/' .env
```

Change the 'SITES=`erp.example.com`' variable for your domain

> Important: You need to preserve the backticks in the variable and add your domain separated by commas without spaces between them.

```bash
sed -i 's/SITES=.*/SITES=`dev-culturac.picurit.com`/' .env
```

## Generate YAML https

```bash
source $BUILDER_PATH/var $BUILDER_PATH
export ERPNEXT_VERSION CUSTOM_IMAGE CUSTOM_TAG PULL_POLICY
docker compose -f compose.yaml \
  -f overrides/compose.mariadb.yaml \
  -f overrides/compose.redis.yaml \
  -f overrides/compose.https.yaml \
  config > $BUILDER_PATH/docker-compose.yml
```

## Start containers

```bash
docker compose \
--project-name atta-erp \
-f $BUILDER_PATH/docker-compose.yml \
  up -d
```

```bash
docker compose \
--project-name atta-erp \
  down
```

## Check proxy logs

```bash
docker compose \
--project-name atta-erp \
  logs -f proxy
```

## Create a new site for production

```bash
docker compose \
--project-name atta-erp \
 exec backend \
 bench new-site dev-culturac.picurit.com \
  --db-name dev-culturac.picurit.com \
  --mariadb-root-password '3rplucky.pr0d' \
  --admin-password 'sys4dm!npr0dZOZE' \
  --no-mariadb-socket \
  --install-app payments \
  --install-app erpnext \
  --install-app hrms \
  --install-app education \
  --install-app whitelabel \
  --install-app erp_improve \
  --install-app healthcare
```

Drop site

```bash
bench drop-site dev-culturac.picurit.com --force
```

Enable scheduler

```bash
bench --site dev-culturac.picurit.com enable-scheduler
```

C0pyGppX!

## Install erp_co app

```bash
docker compose \
--project-name atta-erp \
-f $BUILDER_PATH/docker-compose.yml \
 exec backend \
  bench --site boomb.com.co install-app frappe_better_attach_control erp_col
```



## Enable the scheduler
  
```bash
docker compose \
--project-name atta-erp \
-f $BUILDER_PATH/docker-compose.yml \
 exec backend \
bench --site boomb.com.co enable-scheduler
```

## Check the site health

```bash
docker compose \
--project-name atta-erp \
-f $BUILDER_PATH/docker-compose.yml \
 exec backend \
  bench --site boomb.com.co doctor
```

## Create first backup

```bash
docker compose \
--project-name atta-erp \
-f $BUILDER_PATH/docker-compose.yml \
 exec backend \
  bench --site boomb.com.co backup --with-files
```

## Enter the interactive shell for the frappe container

```bash
docker compose \
--project-name atta-erp \
exec -e "TERM=xterm-color" \
 -it backend bash
```

## Access to database

```bash
docker compose \
--project-name atta-erp \
-f $BUILDER_PATH/docker-compose.yml \
 exec -e "TERM=xterm-256color" \
  -w /var/lib/mysql \
  db mysql -uroot -p3rpt00rpr0d
```

## Editing config manually

Edit `common_site_config.json` or `site_config.json` from sites volume has to be edited using following command

```bash
docker run --rm -it \
  -v nestcolony_sites:/sites \
  -w /sites \
  -e "TERM=xterm-256color" \
  bash
```

```bash
docker run --rm -it \
  -v nestcolony_db-data:/db-data \
  -w /db-data \
  -e "TERM=xterm-256color" \
  bash
```

Show letsencrypt files

```bash
docker run --rm -it \
  -v nestcolony_cert-data:/etc/letsencrypt \
  -w /etc/letsencrypt \
  -e "TERM=xterm-256color" \
  bash
```

Show letsencrypt logs

```bash
docker run --rm -it \
  -v nestcolony_cert-data:/etc/letsencrypt \
  -w /etc/letsencrypt \
  -e "TERM=xterm-256color" \
  bash
```

Enter the interactive shell for the proxy container

```bash
docker compose \
--project-name atta-erp \
-f $BUILDER_PATH/docker-compose.yml \
exec -e "TERM=xterm-256color" \
 -it proxy sh
```

Restart the proxy container

```bash
docker compose \
--project-name atta-erp \
-f $BUILDER_PATH/docker-compose.yml \
restart proxy
```

Stop the proxy container

```bash
docker compose \
--project-name atta-erp \
-f $BUILDER_PATH/docker-compose.yml \
stop proxy
```

Delete the proxy container

```bash
docker compose \
--project-name atta-erp \
-f $BUILDER_PATH/docker-compose.yml \
rm -f proxy
```

Recreate the proxy container

```bash
docker compose \
--project-name atta-erp \
-f $BUILDER_PATH/docker-compose.yml \
up -d proxy
```

Restart the backend container

```bash
docker compose \
--project-name atta-erp \
-f $BUILDER_PATH/docker-compose.yml \
restart backend
```

Restart the frontend container

```bash
docker compose \
--project-name atta-erp \
-f $BUILDER_PATH/docker-compose.yml \
restart frontend
```

