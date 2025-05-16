# *Ask for a date app*
Deploy a fully functional "Ask for a Date" app on a Docker container, accessible via the container, ensuring efficient and scalable deployment.


Let's break down the steps to set up an EC2 instance on AWS and deploy the "Ask for a Date" app.

### Step 1: Set up EC2 on AWS

1. Launch an Amazon EC2 instance:
2. Go to the EC2 console and select "Launch Instance".
3. Choose "Ubuntu" as the Amazon Machine Image (AMI).
4. Follow the prompts to configure the instance details, such as instance type, storage, and security group.

Configure security group:
1. Make sure to allow inbound traffic on port 80, which is the default port used by HTTP.
2. Connect to EC2 via SSH
3. Use the command ssh -i "mykey.pem" `ubuntu@ec2–54–197–62–157.compute-1.amazonaws.com` to connect to your EC2 instance.
Run the following commands

1. `sudo su` to switch to the root user.
2. `apt update` to update the package list.
3. `apt install git` to install Git.
4. `git clone https://github.com/Aakibgithuber/Ask-for-a-date-app.git` to clone the GitHub repository.

### Step 2: Set up Nginx and Docker

1. Install Nginx:
```
sudo apt install nginx
```
2. To start the Nginx service.
```
sudo systemctl start nginx
```
3. To enable Nginx to start on boot.
```
sudo systemctl enable nginx
```
4. To verify that Nginx is running without any errors.
```
sudo systemctl status nginx
```

5. Install Docker:
```
apt-get install docker.io
```
6. To add the current user to the Docker group.
```
usermod -aG docker $USER
```
7. To apply changes.
```
newgrp docker
```
8. To grant full read, write, and execute permissions to all users for the Docker socket file.
```
sudo chmod 777 /var/run/docker.sock
```

### Build and Run Docker Container

1. To build the Docker image.
```
docker build -t my-dating-app
```
2. To run the Docker container and map the container port to your EC2 port.
```
docker run -d --name omegle -p 8081:80 my-dating-app:latest 
```
3. Go to your EC2 instance and add a rule to the security group to open port 8081.
- Access the Application
- Copy the public IP of your EC2 instance and browse to `http://your_public_ip:8081` to access the application.

That's it! You should now have the "Ask for a Date" app up and running on your EC2 instance.🎉🎉
