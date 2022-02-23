# medical-demo


Docker image
(https://hub.docker.com/r/ibmcom/ace-server/)

Pull docker image
docker pull ibmcom/ace-server

Create the initial-config directory
(for example, mine is at /Users/gavinlee@uk.ibm.com/medical/initial-config)

**Create the following folders in this directory:**

setdbparms

setdbparms:
mqsisetdbparms to create security DSN for kafka


Ensure that you have no other aceserver container images running
docker ps

Run the image with the additional parameters required
docker run --name aceserver -p 7600:7600 -p 7800:7800 -p 7843:7843 --env LICENSE=accept --env ACE_SERVER_NAME=ACESERVER --mount type=bind,src=/Users/gavinlee@uk.ibm.com/medical/initial-config,dst=/home/aceuser/initial-config  ibmcom/ace-server:latest

Make sure you are pointing at your local directory for the mount for the initial-config

Once the container is running, check that the initial config overrides are correct
docker exec -it aceserver /bin/bash
Look for the following:
server.conf.yaml 

Connect the toolkit to the server using 127.0.0.1:7600
NOTE: Remember to make sure that the SSL settings are correct for the signer cert

Run the test for the flow - which should work :-)

Have fun!!!
