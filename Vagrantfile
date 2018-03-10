# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = "dummy"
  #config.vm.box = "dimroc/awsdummy"
  #config.vm.box_version = "0.1.0"
 config.vm.provider :aws do |aws, override|
   aws.access_key_id = "AKIAJHUZMABS2WZBZGRQ"
   aws.secret_access_key = "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"
   aws.keypair_name = "MyGSKeyPair"
   aws.ami = "ami-6b933213"
   aws.region = "us-west-2"
   aws.instance_type = "t2.micro"
   aws.security_groups = ['default']

# The Windows version disables the synced folder functionality
# Enable it only if you have rsync installed and in the path
   config.vm.synced_folder '.', '/vagrant', disabled: true
   
#   override.vm.box = "dummy"
   override.ssh.username = "Administrator"
   override.ssh.private_key_path ="C:\\HashiCorp\\Vagrant\\aws\\MyGSKeyPair.pem"
 end
 
   config.vm.provision "shell", inline: <<-SHELL
        sudo yum -y install python-pip
        sudo yum -y install dos2unix
        pip install flask
		pip install redis
        wget https://raw.githubusercontent.com/cermegno/Ansible-test/master/web.py
		# I have removed also the copy of files from the synced folder`
  SHELL
  
end

