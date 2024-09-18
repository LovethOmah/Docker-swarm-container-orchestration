STEPS FOR CONTAINER ORCHESTRATION USING DOCKER SWARM

* I created 2 EC2 Instsnces (This is because i didn't want to use my local machine)

* Name one a manager node and the other a worker node

* Go to your security group and open ports of 2377(docker swarm), 22(SSH), 80(HTTP) 

* Go to your terminal and chmod 400 to secure your keypair

* SSH into the EC2 Instance using the keypair from the console

* Install docker on the two Instances

* On one of the instances do a docker swarm init --advertise-addr <public ip address of manager node>:(to initialize docker on the manager node)

* Copy the token from the manager node on the terminal and paste on the worker node

* Create a service on the manager node using docker service create --name <service name> --publish <ports you are using e.g 80:80> <dockerhub repo/image name>:<version of image>

docker service ls :to list the services you have 
