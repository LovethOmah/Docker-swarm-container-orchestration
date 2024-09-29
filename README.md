STEPS I USED FOR CONTAINER ORCHESTRATION USING DOCKER SWARM


               PROJECT OVERVIEW:
* Container ochestration using docker swarm
* Manager and worker node creation
* Service creation and image deployment
* Scaling of service
* Rollup update
* Rollback update



                PROJECT PREREQUISITES
* Have two EC2s installed
* Make sure to have a keypair
* Make sure your security group have ports 80, 22 and 2377 opened




                 STEPS I USED
* I created 2 EC2 Instsnces (This is because i didn't want to use my local machine)

* Name one a manager node and the other a worker node

* I went to my  security group and open ports of 2377(docker swarm), 22(SSH), 80(HTTP) 

* On my terminal and chmod 400 to secure my keypair

* SSH into the EC2 Instance using the keypair from the console

* Install docker on the two Instances

* On one of the instances do a docker swarm init --advertise-addr <public ip address of manager node>:(to initialize docker on the manager node)

* Copy the token from the manager node on the terminal and paste on the worker node

* Created a service on the manager node and deployed my first image using: docker service create --name docker-swarm --publish 80:80 lovethomah/dragon-mailer:1 

* Docker service ls :to list the services i have.

* I updated the image i previously deployed to a new image by doing a Roll up update using: docker service update --image monyslim/pixer-app:1 docker-swarm

* Did another update to the image using: docker service update --image monyslim/booksfinder:3.1 docker swarm

* Scaled the service and added more containers using: docker service scale docker-swarm=6

* I switched back to the previous version of my deployed image by doing a Roll back update using: docker service update --rollback docker-swarm
