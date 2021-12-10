# cicd-Fail-King

## PART ONE

### Overview

###
    I lost the command now, I had to reboot after an msi update for WSL2 and I can't find it in the history.  But I just followed the link to the repo we needed to create in pilot and copy pasta'ed the command it told me to use.
###


### Docker

###
    I followed the guide found here to install Docker: https://docs.docker.com/engine/install/ubuntu/

        1. Uninstall previous versions of docker just in case:
        sudo apt-get remove docker docker-engine docker.io containerd runc
        
        2. Installing repositories for Docker:
            sudo apt-get update
            
            sudo apt-get install \
            ca-certificates \
            curl \
            gnupg \
            lsb-release

        3. Add docker key:
            curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

        4. Setting up "stable" repository:
            echo \
            "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu \
            $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

        5. Install Docker engine:
            sudo apt-get update
            sudo apt-get install docker-ce docker-ce-cli containerd.io
        
        6. Test to make sure installation is correct:
            sudo docker run hello-world
###

### Dockerfile

###
        1. To create the docker file I created a file called Dockerfile that pulled httpd version 2.4 and copied the web folder to /usr/local/apache2/htdocs/.  EXPOSED port 980 as well but it doesn't actually open the port.

        2. To build the image I used:
             sudo docker build -t web:latest .

        3. To run the container I used:
            docker run -dit -p 8080:80 web

        4. To view the project you must type:
            curl 10.0.0.5:8080
        which is the private ip and the port I bound the container to. to use an external connection I would need to use the elastic ip and 8080 as the port, however, this is not working for me.

### GitHub Actions and DockerHub
    
    1. First, I clicked create a repository ont he home screen.  then made sure private was selected, typed in a name and a description and then off to the races.

    2. I just logged into docker in the terminal... I could not find a setting to change to enable it, so I just went for it and it worked?

    3.  skipped

    4. skipped

### Deployment

    1. I pulled using:
        sudo docker pull ckemplin/project6:latest

        sudo is required only because I am too lazy to put my user in the docker group

    2. I ran the container by running:
        sudo docker run -dit -p 8080:80 web