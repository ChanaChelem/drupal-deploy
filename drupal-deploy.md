https://wodby.com/docs/1.0/stacks/drupal/local/#usage


https://www.drupal.org/docs/user_guide/en/install-dev-making.html
https://www.drupal.org/node/2894005

create a Drupal web with Acquia-dev-desktop, go with the installations
drush sql-dump --gzip --structure-tables-list="cache,cache_*" --result-file='my_db_drupal.sql'


sudo apt install git
git clone https://github.com/ChanaChelem/drupal-deploy.git

<!-- # composer
sudo apt-get install php libapache2-mod-php php-mcrypt php-mysql php-xml
sudo apt install php-cli unzip curl
cd ~
curl -sS https://getcomposer.org/installer -o composer-setup.php
HASH=`curl -sS https://composer.github.io/installer.sig` 
# echo $HASH
php -r "if (hash_file('SHA384', 'composer-setup.php') === '$HASH') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
sudo php composer-setup.php --install-dir=/usr/local/bin --filename=composer
composer -->

<!-- sudo apt install php-xml
sudo apt-get install php-mbstring -->
<!-- sudo apt-get install php libapache2-mod-php php-mcrypt php-mysql php-xml -->

sudo apt-get install mysql-server
sudo apt-get update
sudo apt install unzip curl
<!-- sudo apt-get install docker.io -->
<!-- sudo apt-get install docker-ce docker-ce-cli containerd.io -->

sudo apt-get install apt-transport-https ca-certificates curl gnupg-agent software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo apt-key fingerprint 0EBFCD88
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"

sudo curl -L "https://github.com/docker/compose/releases/download/1.28.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
sudo ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose
docker-compose --version

scp C:\Users\chana\Sites\devdesktop\drupal-8.9.1-deploy\mariadb-init\my_db_drupal.sql.gz  drupal@172.29.146.41:\my_db_drupal.sql.gz

cd drupal-deploy
mkdir mariadb-init
mv my_db_drupal.sql.gz mariadb-init/

sudo docker-compose up -d --build

 http://drupal.docker.localhost:8000

sudo docker container ls
sudo docker exec -it my_drupal8_project_php  /bin/bash
wodby@php.container:/var/www/html $
```
git pull
composer install // first time and in case other developers made changes.
drush cr // Clear caches

? drush updb //Apply database updates
? drush cim -y //Import configuration (in case other developers made changes) 

drush cex -y // export configuration

```  
Error: 'MIME type ('text/html') is not a supported stylesheet MIME type, and strict MIME checking is enabled.'
Solution:
```
drush -y config-set system.performance css.preprocess 0
drush -y config-set system.performance js.preprocess 0
```



sudo docker-compose down --volume

<!-- docker-compose exec mariadb sh -c 'exec mysqldump --all-databases -uroot -p"root-password"' > databases.sql -->