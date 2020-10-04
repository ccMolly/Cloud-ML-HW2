# vg-mnist
Mingxi Chen mc7805@nyu.edu


**This repo provides a Vagrant file with Docker pre-installed and a Dockerfile for running mnist in the virtual box.**

## Structure

	vg-mnist/
	│
	├── README.md                            
	├── Vagrantfile                  
	└── pytorch-cli/ 
	    │                    
	    ├── Dockerfile 
	    ├── pytorch-train.yaml           
	    ├── pytorch-mnist/
	    │   │                     
	    │   ├── main.py
	    │   ├── requirements.txt
   
			

## Build Docker Image
	vagrant up

	vagrant ssh

	cd /vagrant/pytorch-cli

	docker build -t mnist .

## Run
	docker run -it mnist


