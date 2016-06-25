Please refer to 'Project Description.txt' for detailed information about the project.

To run the program please follow these instructions:

1. Please setup Apache Spark and Jupyter. I used vanilla spark local deployment on azure. 
	If you have spark 1.6.x + jupyter running anywhere else, you are free to use that.

2. Instructions for deploying spark 1.6.x + jupyter on Azure.
-> Connect to your Azure portal.
-> Create a classic virtual machine with ubuntu 14.04 LTS
-> Make sure to select classic deployment model
-> Choose a HOSTNAME, username, password, and set the pricing tier to A2 Basic.
-> In “optional configuration”, select “endpoints” and add a ‘jupyter’ endpoint, with private and public ports set to 8888.
-> Make sure to hit OK wherever you need, then hit Create. (Creation might take up to 15 minutes).
-> Once you’ve created, ssh to the server - it will likely be [vm name].cloudapp.net.
-> Install docker (follow the Ubuntu 14.04 LTS directions) from here: docker
-> Create a directory for notebooks, mkdir notebooks (within your home directory)
-> Edit the file /etc/default/docker (via sudo) and add this line: DOCKER_OPTS="-g /mnt"
-> Restart the docker daemon: sudo service docker restart
-> Create the ~/notebooks/ directory (mkdir ~/notebooks/), and if it already exists, make sure it is owned by your userid - 
	if you log in with the username krishna, you can ensure this by running the command chown krishna:krishna ~/notebooks.
-> Run the spark jupyter docker image: sudo docker run -d -p 8888:8888 -v ~/notebooks/:/home/jovyan/work jupyter/all-spark-notebook (this step takes a while)
-> Now attempt to connect to http://HOSTNAME.cloudapp.net:8888,. Please replace HOSTNAME with your VM's hostname.

3. Place the files 'tweet_classifier.ipynb', 'data/train.csv' and 'data/test.csv' files in the Jupyter notebook. 

4. You should be able to run the code now.

Please refer to results.txt for the details about the experimentation done after the classifier construction.