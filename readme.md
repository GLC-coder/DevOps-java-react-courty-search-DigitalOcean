# Java-React Country Search project deployed on Droplets DigitalOcean

Java-React App URL : http://128.199.214.234:7071

Create an server and deploy the application developed in React, Redux and Java on Droplets DigitalOcean

## Technologies used:

DigitalOcean, Linux, Java, Gradle, React, Redux

## Project Description:

1- Setup and configure a server on DigitalOcean.

2- Configure SSH on the firewall for the server.

3- Create and configure a new Linux user on the Droplet for best security practice.

4- Deploy and run a Java Gradle application on the Droplet.

## Instructions

### Step 1 : Create a server on DigitalOcean

1- Sign up an account on the DigitalOcean and configure SSH keys.

2- Create a Droplet for Java-React Country Search Project with Linux Ubuntu distribution in Singapore Region by configuring the authentication method with SSH Key instead of Password.

3- Turn on the firewall for the server and configure the SSH with port 22 and specific ip address for Inbound traffics.

### Step 2 : Prepare the server on DigitalOcean

#ssh into the newly created server

```
ssh -i .ssh/id_rsa root@128.199.214.234
```

#update apt and install java 8 on the server

```
update apt
```

```
apt install openjdk-8-jre-headless
```

### Step 3 : Build Jar file

#Open the Java-React App in the Visual Studio Code and build the Java-React App into Jar file

```
./gradlew build
```

### Step 4 : Copy built Java-React App file into the remote server

#Secure copy the built Java-React App file from local machine to server. Execute from project's root folder

```
scp -i .ssh/id_rsa build/libs/java-react-app-example.jar root@128.199.214.234:/root
```

### Step 5 : Run the Java-React App on the Remote Server

#Ssh into droplet / remote server as root user

```
ssh -i .ssh/id_rsa root@128.199.214.234
```

#Run the Java-React App on the Remote Server as the attached mode

```
java -jar java-react-app-example.jar
```

#Get the current running processes info, including the Port and process ID

![image](https://github.com/GLC-coder/DevOps-java-react-courty-search-DigitalOcean/blob/master/IMG/Screenshot%202023-01-25%20at%2012.02.49%20am.png)

```
netstat -lpnt
```

#run the Java-React App on the Remote Server as detached mode

```
java -jar java-react-app-example.jar &
```

#Stop run the Java-React App from the detached mode

```
kill <PID>
```

### Step 6 : Update the firewall rules

![image](https://github.com/GLC-coder/DevOps-java-react-courty-search-DigitalOcean/blob/master/IMG/Screenshot%202023-01-24%20at%2011.48.34%20pm.png)

1-Update the firewall rules with the server listening port number: 7071 for all ip address in inbound traffic.
![image](https://github.com/GLC-coder/DevOps-java-react-courty-search-DigitalOcean/blob/master/IMG/Screenshot%202023-01-24%20at%2011.53.09%20pm.png)

### Step 7 : Visit the Java-React App with the public ipv4 and port number of the server.

URL : http://128.199.214.234:7071/
![image](https://github.com/GLC-coder/DevOps-java-react-courty-search-DigitalOcean/blob/master/IMG/Screenshot%202023-01-24%20at%2011.55.47%20pm.png)
### Step 8 : Add Normal Linux User

#Add a normal linux user and assign the user with root privileges.

```
adduser jason
```

#Assign the user into sudo group

```
usermod -aG sudo jason
```

#Add the public key into .ssh folder at the jason root folder

```
mkdir .ssh
```

#Copy the public key of the computer into authorized_keys under the .ssh folder via Vim editor

```
sudo vim .ssh/authorized_keys
```

#Exit the server from root user and login with the new created user

```
exit
```

```
exit
```

```
ssh .i .ssh/id_rsa jason@128.199.214.234
```
![image](https://github.com/GLC-coder/DevOps-java-react-courty-search-DigitalOcean/blob/master/IMG/Screenshot%202023-01-25%20at%2012.11.08%20am.png)
