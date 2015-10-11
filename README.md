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
    




    
    

