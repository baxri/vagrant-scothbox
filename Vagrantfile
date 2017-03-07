# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
		
	config.vm.provider "virtualbox" do |vb|
		vb.customize ["modifyvm", :id, "--memory", "256"]
	end
		
    config.vm.box = "scotch/box"
    config.vm.network "private_network", ip: "192.168.10.20"
    config.vm.hostname = "scotchbox"
    config.vm.synced_folder ".", "/var/www", :mount_options => ["dmode=777", "fmode=666"]
    
    # Optional NFS. Make sure to remove other synced_folder line too
    #config.vm.synced_folder ".", "/var/www", :nfs => { :mount_options => ["dmode=777","fmode=666"] }
	
	config.vm.provision "shell", inline: <<-SHELL
   
		sudo cp /var/www/sites/vhosts /etc/apache2/sites-available/vhosts.conf		
		sudo a2ensite vhosts		
		
		sudo service apache2 restart		
	
    SHELL
	
	config.vm.box_download_insecure = true
end
