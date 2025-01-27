# CKAN---Installation

This page will help you to run the CKAN in Ubantu 22.04 through Docker and Docker Compose.

The complete installation guide is as fellows:


## Installing Docker and Docker Compose
#### Step 1: Update your system

First, make sure your system is up to date:

`sudo apt update`   
`sudo apt upgrade -y`

#### Step 2: Install dependencies

Install necessary packages:

`sudo apt install apt-transport-https ca-certificates curl software-properties-common -y`  

#### Step 3: Add Docker's official GPG key

Add Docker’s official GPG key to verify the authenticity of the packages:

`curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg`

#### Step 4: Add Docker repository

Add Docker’s stable repository to your system:

`echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null`

#### Step 5: Install Docker

Now, install Docker:

`sudo apt update`      
`sudo apt install docker-ce docker-ce-cli containerd.io -y`

#### Step 6: Start and enable Docker service

Ensure Docker starts automatically at boot and start the service:

`sudo systemctl enable --now docker`

#### Step 7: Verify Docker installation

Check if Docker is installed and running:

`sudo docker --version`  

#### Step 8: Install Docker Compose

To install Docker Compose, you need to download the binary.

    Download the latest version of Docker Compose:

`sudo curl -L "https://github.com/docker/compose/releases/download/v2.19.0/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose`

Set executable permissions on the binary:

`sudo chmod +x /usr/local/bin/docker-compose`

#### Verify the installation:

`docker compose --version`




## Installing CKAN (2.11)

I installed through WSL –root (Ubantu 22.04)
`lsb_release -a`
`git clone[ https://github.com/ckan/ckan-docker.git](https://github.com/ckan/ckan-docker.git)`
`cp .env.example .env`
`read this env.example file from the github repo for better understanding`
`nano .env`
`cd ckan-docker`
#### [Option 1] To build CKAN in base mode (If you don't want to modify templates and other resources)
`docker compose up -d –build`     
Create User after installation  (set email and password of your choice)     
`docker compose exec ckan ckan user add admin email=[xxxxxx@example.com] password=[Password]`     
Make the created user sysadmin so that you have access to all privilege    
`docker compose exec ckan ckan sysadmin add admin`    
Access CKAN Instance running on link below     
`https://localhost:8443/`      
#### [Option 2] To build CKAN in developnebt mode (if you want to modify templates etc.)      
`docker compose -f docker-compose.dev.yml up -d --build`     
Create User after installation  (set email and password of your choice)     
`sudo docker compose exec ckan-dev ckan user add admin email=[xxxxxx@example.com] password=[Password]`     
Make the created user sysadmin so that you have access to all privilege    
`docker compose exec ckan-dev ckan sysadmin add admin`   
Access CKAN Instance running on link below
`https://localhost:5000/`

#### Further go to login page login with the credentials that you have created before:
`Username: [email]`
`Password: [Password]`
#### Make an organization
#### Upload dataset from this organization
 
To re-run the setup:
1.      Move to the ckan-docker folder
2.      Run the commands:
*  `docker compose build` 
* `docker compose up`
* `https://localhost:8443/` or `https://localhost:5000/`
 
Refer to the documentation for further exploration of the CKAN functionalities[ https://docs.ckan.org/en/2.11/contents.html](https://docs.ckan.org/en/2.11/contents.html)
