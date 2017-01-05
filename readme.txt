sudo puppet apply /vagrant/manifests/web.pp

sudo service tomcat7 restart

vagrant plugin install vagrant-aws

vagrant up --provider=aws
