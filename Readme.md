End-to-End DevOps Pipeline for a Node.js Web Application using Jenkins, Docker, and AWS
________________________________________
1.	Project Description
This project demonstrates a complete DevOps pipeline for deploying a Node.js web application using modern DevOps tools and practices. The application source code is hosted in a Git repository and automatically built and deployed using a CI/CD pipeline.
The application is containerized using Docker and deployed on an AWS EC2 instance. Monitoring is implemented using Prometheus, Node Exporter, and Grafana to observe system and application metrics.
The main goal of this project is to automate the build, deployment, and monitoring process using DevOps practices.
________________________________________
Tech Stack
Layer                   -	  Tools Used
Source Control   -	 Git, GitHub
CI/CD                    -	  Jenkins
Containerization -   	  Docker, Docker Hub
Cloud Platform	- AWS EC2
Monitoring	- Prometheus, Node Exporter, Grafana
Application	- Node.js web appli
	________________________________________
•	GIT
Clone the Repository
git clone https://github.com/santhoshkumardevendran/capstoneproject
git add <file-name>
git commit -m "commit message"
git push origin main
________________________________________
•	JENKINS
Install Application Dependencies -  npm install
sudo apt update
sudo apt install openjdk-17-jdk -y
sudo systemctl start jenkins
sudo systemctl enable Jenkins
http://EC2-IP:8080
________________________________________
•	DOCKER
docker --version
sudo systemctl start docker
sudo systemctl enable docker
docker build -t santhoshkumardevendran/node-app .
docker images
docker ps
________________________________________
•	DOCKER HUB
docker login -u santhoshkumardevendran -p ******
docker push santhoshkumardevendran/node-app
•	Deploy container to EC2
docker run -d -p 3000:3000 --name  santhoshkumardevendran/node-app
________________________________________
•	NODE-EXPORTER
# Download latest version
wget https://github.com/prometheus/node_exporter/releases/download/v1.10.2/node_exporter-1.10.2.linux-amd64.tar.gz

# Extract files
tar xvfz node_exporter-1.10.2.linux-amd64.tar.gz

# Move binary to /usr/local/bin
sudo mv node_exporter-1.10.2.linux-amd64/node_exporter /usr/local/bin/

# Run manually
/usr/local/bin/node_exporter

# Access metrics on browser
http://EC2-IP:9100/metrics
sudo systemctl daemon-reload
sudo systemctl start node_exporter
sudo systemctl enable node_exporter
sudo systemctl status node_exporter
________________________________________
•	PROMETHEUS - Connect via SSH
ssh -i " key.pem" ubuntu@public -ip
#Download Prometheus
wget https://github.com/prometheus/prometheus/releases/download/v3.10.0/prometheus-2.47.0.linux-amd64.tar.gz
tar xvfz prometheus-3.10.0.linux-amd64.tar.gz
sudo nano /etc/systemd/system/prometheus.service
sudo systemctl daemon-reload
sudo systemctl start prometheus
sudo systemctl enable prometheus
sudo systemctl status Prometheus
________________________________________
•	GRAFANA
sudo apt install grafana -y
wget -q -O - https://packages.grafana.com/gpg.key | sudo apt-key add -
sudo systemctl start grafana-server
sudo systemctl enable grafana-server
sudo systemctl status grafana-server
________________________________________
•	CRON JOB
crontab -l
crontab -e
0 2 * * * /home/ubuntu/backup.sh (0 2 * * * /home/ubuntu/backup.sh)
sudo systemctl start cron
sudo systemctl enable cron
sudo systemctl status cron
________________________________________
•	CI/CD flow explained briefly
In my project, the CI/CD pipeline automates the process of building, testing, and deploying a Node.js application. The pipeline integrates several DevOps tools to ensure faster and reliable application delivery.
1. Code Commit
The developer writes code for the Node.js application and pushes it to the repository hosted on GitHub.
2. Continuous Integration
Whenever code is pushed to GitHub, Jenkins automatically triggers the CI pipeline. Jenkins pulls the latest code from the repository and starts the build process.
3. Build and Test
During the build stage, the application dependencies are installed and the application is tested to ensure that the code works correctly without errors.
4. Containerization
After a successful build, the application is packaged into a container using Docker. This creates a Docker image that contains the Node.js application and its required dependencies.
5. Deployment
The Docker image is deployed to an EC2 instance on Amazon Web Services where the application runs inside a Docker container.
6. Monitoring
The deployed application and server resources are monitored using Prometheus and visualized through dashboards in Grafana.
Summary
This CI/CD pipeline automates the entire process from code integration to deployment and monitoring, ensuring that the Node.js application is delivered quickly, efficiently, and with minimal manual intervention.






