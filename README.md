#How to install Teamcity Build Agent on Ubuntu Server

Download the build agent from your server

    
    mkdir /srv/buildAgent
    cd /srv/buildAgent
    wget http://<teamcityserver>:8111/update/buildAgent.zip
    
Unzip the build agent

    sudo zip buildAgent.zip
    sudo rm buildAgent.zip
    
Configure the location of the server

    sudo cp conf/buildAgent.dist.properties conf/buildAgent.properties
    sudo nano conf/buildAgent.properties 
    #change the following line
    serverUrl=http://serverLocation:8111/
    
Make bin folder executable

    sudo chmod u+x bin/*.sh

Edit rc.local to start the service at server startup

    sudo nano /etc/rc.local
    
Add the following line before exit 0

    /srv/buildAgent/bin/agent.sh start

Reboot 

    sudo shutdown -r now
    
Additionally, if front end tools (node/grunt) are required do the following

    sudo apt-get update
    sudo apt-get install --yes nodejs
    
In my case, I needed to compile and install native add-ons

    apt-get install --yes build-essential
    
Finally, another option is to install nodejs using the node version manager

    sudo apt-get install build-essential libssl-dev
    curl https://raw.githubusercontent.com/creationix/nvm/v0.16.1/install.sh | sh
    
After the install, check the versions typing the following:
    
    #make sure you are using bash, other shells may fail finding nvm ie. zsh)    
    nvm ls-remote
    nvm install 0.12.7
    
    



    
    

