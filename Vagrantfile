Vagrant.configure(2) do |config|  

  config.vm.box = "ubuntu_aws"
  config.vm.box_url = "https://github.com/mitchellh/vagrant-aws/raw/master/dummy.box"

  config.vm.provider :aws do |aws, override|
    aws.access_key_id = "SUA_CHAVE"
	  aws.secret_access_key = "SUA_CHAVE_SECRETA"

    aws.keypair_name = "palestra-devops"
    aws.ami = "ami-5189a661"
    aws.security_groups = ['devops-vagrant']
    aws.region = "us-west-2"

    override.ssh.username = "ubuntu"
    override.ssh.private_key_path = "palestra-devops.pem"
  end

  config.vm.define :web do |web_config|
    web_config.vm.network "private_network", ip: "192.168.50.10"
    web_config.vm.provision "shell", path: "manifests/bootstrap.sh"
    web_config.vm.provision "puppet" do |puppet|
      puppet.manifest_file = "web.pp"
    end

    web_config.vm.provider :aws do |aws|
      aws.tags = { 'Name' => 'MusicJungle (vagrant)'}
    end
  end
end
