# Deploy-Nexus-as-Docker-container
### Run Nexus as Docker Container on DigitalOcean Droplet

### Technologies used:
Docker, Nexus, DigitalOcean, Linux

### Project Description:
Create and Configure Droplet
Set up and run Nexus as a Docker container

Below are the general steps to run Nexus as a Docker container on a DigitalOcean droplet:

Step 1: Create a new Droplet on DigitalOcean, choose a plan that suits your needs and select the Docker image option under the "Choose a configuration" section.

Step 2: Once the droplet is created, SSH into the droplet.

Step 3: Install Docker on the droplet using the following commands:

    sudo apt update
  sudo apt install docker.io
  
Step 4: Pull the latest Nexus 3 image from Docker Hub using the following command:

  sudo docker pull sonatype/nexus3

Step 5: Create a Docker volume to persist Nexus data using the following command:

  sudo docker volume create nexus-data

Step 7: Start the Nexus container using the following command:

  sudo docker run -d -p 8081:8081 --name nexus -v nexus-data:/nexus-data sonatype/nexus3
  
This command starts the Nexus container in detached mode (-d), maps the container port 8081 to the host port 8081 (-p 8081:8081), sets the container name to "nexus" (--name nexus), and mounts the Docker volume named "nexus-data" to the container's /nexus-data directory (-v nexus-data:/nexus-data).

Step 8: Wait a few minutes for Nexus to start up. You can check the Nexus logs using the following command:

  sudo docker logs -f nexus

Step 9: Once Nexus is up and running, you can access it using your Droplet's IP address and port 8081 (e.g., http://your-droplet-ip-address:8081). Follow the on-screen instructions to complete the Nexus setup process.

That's it! You now have Nexus running as a Docker container on a DigitalOcean droplet.

