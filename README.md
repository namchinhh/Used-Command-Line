# Used-Command-Line
scp -P 17177 darelloc@vm785.fcomet.com:~/public_html/backup301217.sql /var/www/html/darello

git config core.fileMode false  

// turn on debug
php bin/magento config:set dev/debug/debug_logging 1 && php bin/magento cache:flush

php -dmemory_limit=6G bin/magento setup:static-content:deploy

\Magento\Framework\App\ObjectManager::getInstance()->get('Psr\Log\LoggerInterface')->debug("abc".print_r($var,true)."\n");

$now = strtotime(date('Y-m-d H:m:s'));


\\ Fix role root in apache2 terminal
subl /etc/apache2/envvars
export APACHE_RUN_USER=namnt
export APACHE_RUN_GROUP=namnt
sudo chown namnt:namnt -R .

//install php 7.1
sudo add-apt-repository ppa:ondrej/php
sudo apt-get update
sudo apt install php7.1

//install php 7.1 extension
sudo apt-get install php7.1-dom php7.1-curl php7.1-gd php7.1-mcrypt php7.1-intl php7.1-mbstring php7.1-mysql php7.1-soap php7.1-zip php7.1-bcmath php7.1-dev

sudo service apache2 restart

//install ioncube

wget http://downloads3.ioncube.com/loader_downloads/ioncube_loaders_lin_x86-64.tar.gz

cd ioncube

sudo cp ioncube_loader_lin_7.1.so /usr/lib/php/20160303/
sudo nano /etc/php/7.1/apache2/conf.d/00-ioncube.ini

paste vao 
	zend_extension = "/usr/lib/php/20160303/ioncube_loader_lin_7.1.so"
sudo service apache2 restart

vao phpinfo() xem da cai xong ioncube chua


//switch giua 2 version 7.0 va 7.1

Sang 7.0 

sudo a2enmod php7.0 && sudo a2dismod php7.1 && sudo update-alternatives --set php /usr/bin/php7.0 && sudo update-alternatives --set php-config /usr/bin/php-config7.0 && sudo update-alternatives --set phpize /usr/bin/phpize7.0  && sudo service apache2 restart

Sang 7.1

sudo a2enmod php7.1 && sudo a2dismod php7.0 && sudo update-alternatives --set php /usr/bin/php7.1 && sudo update-alternatives --set php-config /usr/bin/php-config7.1 && sudo update-alternatives --set phpize /usr/bin/phpize7.1  && sudo service apache2 restart

Anh em nho cai lai xdebug cho 7.1

//generate ssh key
ssh-keygen
cat ~/.ssh/id_rsa.pub

//create custom debug.log
$writer = new \Zend\Log\Writer\Stream(BP . '/var/log/templog.log');
$logger = new \Zend\Log\Logger();
$logger->addWriter($writer);
$logger->info("debug in here");

/////DOCKER
docker exec -it kathmandu_php-fpm_1 bash

// down tool 
docker exec -itu www kathmandu_php-fpm_1 bash -c "cd /tmp/ && composer create-project --repository=https://repo.magento.com magento/marketplace-eqp magento-coding-standard"

//check phpcs
docker exec -itu www kathmandu_php-fpm_1 bash -c "cd /tmp/magento-coding-standard; ./vendor/bin/phpcs /var/www/current/src/app/code/Kathmandu/SummitClub --standard=MEQP2 --extensions=php,phtml --exclude=Generic.PHP.DisallowShortOpenTag"

//fix phpcs
docker exec -it kathmandu_php-fpm_1 bash -c "cd /var/www/current/src; ./vendor/bin/php-cs-fixer fix --config=.php_cs.kathmandu -v --using-cache=no"

ssh -i uat-goodbrand_\(3\).pem ubuntu@devgb.goodbrand.com.au

rm -rf cache/* amasty_fpc/* locks/*                             
