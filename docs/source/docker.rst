#######################
Get started with Docker
#######################

Install Docker
==============

Docker is available on multiple platforms. Check the following link to choose the best installation path for you:
	
	-	`Docker for Mac (macOS) <https://docs.docker.com/docker-for-mac/install>`_
	-	`Docker for Windows (Microsoft Windows 10) <https://docs.docker.com/docker-for-windows/install>`_

If the above does not fulfil your requirements follow the link `here <https://docs.docker.com/engine/installation/>`_ .

Create & Execute the Dockerfile
===============================

Docker automatically build images by reading the instructions you provide in the ``Dockerfile``. A ``Dockerfile`` is a text document that contains all the command a user could call on the command line to assemble an image.

The ``Dockerfile`` must start with the ``FROM`` instruction. Below is an example of a ``Dockerfile`` ::

		# base image
		FROM ubuntu:latest

		# clean and update sources
		RUN apt-get clean && apt-get update

		# install basic apps
		RUN apt-get install -qy nano

		# install Python and modules
		RUN apt-get install -qy python3
		RUN apt-get install -qy python3-psycopg2


Follow this `link <https://docs.docker.com/engine/reference/builder/>`_ to know more about creating a ``Dockerfile``.

-	To login into your account ::

		$ docker login

-	Executing the ``Dockerfile`` commands ::

		To directly execute the file command use:
		$ docker build . (With this command <none> repo is created. To avoid this use the next command)
		Sending build context to Docker daemon 5.51 MB
		...

		You can specify the name of the repository with:
		$ docker build -t your_name .

View all the Images
===================

-	To view all the top level images run ::

		$ docker images

		The output:

 		REPOSITORY   TAG      IMAGE ID       CREATED         SIZE
 		----------------------------------------------------------
		your_name    latest   d6e415a70abf   8 seconds ago   210MB
		ubuntu       latest   747cb2d60bbe   2 weeks ago     122MB

	The above output states that the repository ``ubuntu`` is the base image, because of the ``FROM ubuntu:latest`` command in the Dockerfile.

	The ``your_name`` image is the combination of all the packages mentioned in the Dockerfile.


-	To delete the images ::

		$ docker rmi image_id

Containers
==========

Docker containers ensures that the software will behave the same way, regardless of where it is deployed, because its runtime environment is ruthlessly consistent.

-	To create a container in your image use ::

		$ docker run -ti image_name

		Where :  
			-	t : gives us the terminal
			-	I : allows us to interact with the terminal

		Output - root : root@contaner_id:/#

-	To exit from the container ::
	
		root : root@contaner_id:/# exit

-	To Check all containers in your image ::
		
		To list all the containers:
		$ docker ps -a      

		To check the running container:
		$ docker ps 

-	To delete the container ::

		$ docker rm contaner_id


Image to Docker Cloud
=====================

-	Search command to find suitable image ::

		$ docker search image_name 

	Below is a screenshot for : ``docker search ubuntu``

	IMAGE.

-	To pull the image ::

		$ docker pull username/repo_name:tag_Name    

-	To commit the image ::

		$ docker tag IMAGE_ID username/repo_name:tag_Name     

-	To push image ::

		$ docker push username/repo_name:tag_Name    


