## Jenkins Installation and Configuration Guide ##

### 1. Install Jenkins ###

sudo wget -O /usr/share/keyrings/jenkins-keyring.asc \
  https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key

echo "deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc]" \
  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null

sudo apt-get update
sudo apt-get install jenkins -y

### 2. Install Java (Required for Jenkins) ###

sudo apt update
sudo apt install fontconfig openjdk-17-jre -y
java -version

### 3. Enable and Start Jenkins Service ###

sudo systemctl enable jenkins  
sudo systemctl start jenkins
sudo systemctl status jenkins

4. Enable Security Port in AWS EC2 (8080 for Jenkins)

Go to AWS EC2 Security Groups.

Find the Security Group associated with your instance.

Edit Inbound Rules.

Add a new rule:

Type: Custom TCP Rule

Port Range: 8080

Protocol: TCP

Source: Anywhere (0.0.0.0/0) or a specific IP for security.

Save the changes.

## 5. Get Initial Admin Password ##

sudo cat /var/lib/jenkins/secrets/initialAdminPassword

Copy the displayed password.

Use it for the initial Jenkins setup at http://your-ec2-instance-ip:8080.
