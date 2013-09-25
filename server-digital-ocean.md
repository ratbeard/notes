https://www.digitalocean.com/community/articles/initial-server-setup-with-ubuntu-12-04

Created droplet in web ui.  Ubuntu 13.04x64
Got connection info from email.  
Login, change password

		ssh root@192.241.248.44
		passwd
	
Create user, give sudo

		adduser mfrawley
		visudo
		# Add line in privilege specification:
		mfrawley ALL=(ALL:ALL) ALL
	
Turn off ssh for root:

		vi /etc/ssh/sshd_config
		# Edit:
		PermitRootLogin no
	
Login with user:

		ssh mfrawley@192.241.248.44
		
Upload ssh pub key:

		cat ~/.ssh/id_rsa.pub | ssh mfrawley@192.241.248.44 'mkdir -p ~/.ssh && cat >> ~/.ssh/authorized_keys'
		
Install nginx

		sudo apt-get install nginx
		sudo service nginx start
		# get ip and visit in browser
		ifconfig eth0 | grep inet | awk '{ print $2 }'
		# ensure loads on reboot

Install fail2ban

		sudo apt-get install fail2ban
		# I did some configuration, but don't think its really needed - just changed my computer ip, but thats dynamic anyways.  Not sure if need to create `.local` config file name.  Setting up w/ email would be dece
		# Verify iptables setup
		sudo iptables -L
		
		
Install Go

		sudo apt-get update
		sudo apt-get install linux-image-extra-`uname -r`
		# Pick 'Keep installed grub' in menu
		wget http://go.googlecode.com/files/go1.1.1.linux-amd64.tar.gz
		tar xf go1.1.1.linux-amd64.tar.gz
		rm go1.1.1.linux-amd64.tar.gz
		
		vi ~/.bashrc
		# Add:
		export GOROOT=$HOME/go
		export GOPATH=$HOME/gocode
		export PATH=$PATH:$GOROOT/bin:$GOPATH/bin
				
Install Docker from source

		sudo apt-get install lxc curl xz-utils git mercurial
		mkdir -p $GOPATH/src/github.com/dotcloud
		cd !$
		git clone https://github.com/dotcloud/docker.git
		go get -v github.com/dotcloud/docker/...
		# Link 'docker' so root can run it:
		sudo ln -s $GOPATH/bin/docker /usr/local/bin/docker
		
Run docker

		sudo docker -d & 

Install node/coffee

		sudo apt-get update
		sudo apt-get install python-software-properties python g++ make
		sudo apt-get install software-properties-common
		sudo add-apt-repository ppa:chris-lea/node.js
		sudo apt-get update
		sudo apt-get install nodejs
		sudo npm install -g coffee

Install tmux
		
		sudo apt-get install tmux



# Deploying Node

Make user and dir

		sudo adduser imgoblin  # enter pw
		sudo groupadd www
		sudo adduser imgoblin www
		sudo mkdir /www
		sudo chown mfrawley:www /www
		cd /www
		git clone https://github.com/ratbeard/imgoblin.git
		cd imgoblin

Edit ngingx conf:

		sudo vi /etc/nginx/sites-available/default
		# Edit Config:
		# needed this in http config:
		server_names_hash_bucket_size 64;
		made a default server that 404's

		sudo nginx -s restart


Build static site:

		cd /www/imgoblin
		npm install
		sudo npm install -g grunt-cli bower nodemon
		bower install
		mv bower_components app # wtf - why works locally?
		grunt build # had to tweak gruntfile to work - turn off svg, turn of rev for images.

Run nodejs server:
	
		cd /www/imgoblin
				

		
