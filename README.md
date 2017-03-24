# sfdocker

* Install bpkg:

sudo -s

curl -Lo- "https://raw.githubusercontent.com/bpkg/bpkg/master/setup.sh" | bash

* Download/Update package:

cd app/

bpkg install lopezator/sfdocker

* Link library within composer.json (post-install && post-update):

cd ../

ln -s app/deps/bin/sfdocker sfdocker

* Set  default container name value in your Symfony's parameters.yml (php-fpm container) like this:

sfdocker_default_container: myproject-php-fpm

Commands inside the docker wrapper
==================================

1.- Docker containers handling:
------------------------------

* Start docker:

./sfdocker start

* Stop docker:

./sfdocker stop

* Restart docker:

./sfdocker restart

* Destroy docker:

./sfdocker destroy

* Enter in docker (default value: <sfdocker_default_container>)
<-p> optional modifier starts the container as privileged user (root):

./sfdocker enter <container> <-p>

* Show running containers:

./sfdocker ps

* Docker logs (default value: <sfdocker_default_container>):

./sfdocker logs <container/all>

2.- Symfony handling & code tools:
----------------------------------

* Execute symfony console:

./sfdocker console <args>

* Clear symfony cache (default value: dev):

./sfdocker cache <dev/prod/test/all>

* Check code compliance:

./sfdocker ccode

* Run composer:

./sfdocker composer <args>

(Starts composer inside the container, so you can send any other composer parameter 
, if it's wrong, composer itself will return the error).