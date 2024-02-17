# UNDERSTANDING MAVEN: BUILDING A SIMPLE SPRING BOOT JAVA PROJECT
![](Logo.png)

*This project demonstrates the creation of a simple Spring Boot Java project using Maven. It starts with generating project structure via Spring Initializr. Then, it guides through creating Java source code. Next, it involves setting up an EC2 instance on AWS and connecting via MobaXterm. Configurations are done to ensure Maven works, followed by verifying Maven by compiling and building the Java code on EC2. This hands-on project provides practical insights into Maven, AWS setup, and Java project management in a cloud environment.*


# Learning Outcomes

  - Gain proficiency in setting up a Spring Boot Java project using Maven.
  - Understand the process of generating project structure with Spring Initializr.
  - Learn to write and manage Java source code within a Spring Boot project.
  - Acquire skills in setting up and configuring an EC2 instance on AWS.
  - Develop competency in connecting to an EC2 instance using MobaXterm.
  - Learn to install and configure Maven on an EC2 instance.
  - Practice compiling and building Java code using Maven on a remote server.
  - Gain insights into cloud-based development workflows and infrastructure management.
  - Enhance problem-solving skills by troubleshooting and resolving configuration issues.
  - Develop a deeper understanding of software development best practices within a cloud environment.

# Prerequisites 


  - `Basic` understanding of Java programming language. 
  - Familiarity with `Spring Boot framework` concepts (e.g., dependency injection, annotations).
  - Basic understanding of `Maven` build tool and its usage.
  - Knowledge of `AWS services` and basic familiarity with the AWS Management Console.
  - Understanding of `remote server access` concepts (e.g., `SSH`).
  - Basic familiarity with `terminal/command line interfaces`.
  - Access to an AWS account with `permissions` to create and manage EC2 instances.
  - Installation of `MobaXterm ` or equivalent `SSH client for remote server access`.
  - Familiarity with software development concepts such as `compiling`, `building`, and `configuring` applications.


# LET'S START

# STEP1 : Generate Project Structure

Utilize Spring Initializr to generate the initial structure for the Spring Boot Java project with Maven.

- Go to https://start.spring.io/ 
- Choose the options like in the picture1;
  - Project: Maven
  - Spring Boot : 3.2.2
  - Name: Give a name for your artifacts
  - Packaging : Jar
  - Language : Java

![](spring.io/springio-1.png)

  - Add `Spring Web` and `Spring Reactive Web ` dependencies.

![](/spring.io/simpringio-2.PNG)

  - And (generate) download it to your computer.

![](./spring.io/sipringio-3.PNG)


- After downloading the zip file create a `project folder` and extract inside of the folder.
- It will look like following image. 

![](./spring.io/springio-4.PNG)

- Now we have `java project` source code. Let's start configuring other environments.


# STEP2: Download MobaXterm

- What is MobaXterm and why we use it? 
   - MobaXterm is a versatile and popular terminal emulator and remote desktop client for Windows. It integrates essential tools like SSH, X11 server, RDP, and file transfer capabilities into a single application, making it convenient for developers, system administrators, and IT professionals to manage remote servers and perform system administration tasks from their Windows machines. It's widely used for its intuitive interface, extensive feature set, and ease of use, offering a seamless experience for accessing and controlling remote systems efficiently.

- Go to https://mobaxterm.mobatek.net/download.html and choose `Free Version` and download the `MobaXterm Home Edition v23.6 (Portable Edition)` zip file and extract it. 

- You will see the `personal exe` file just clock it, it will just open immidiately. 

![](/MobaXterm/exe-file.PNG)

*Note: If you are using other tools (ex; VSCode ) to connect remote machines it is fine to use your tool. I just want to show you a different tool to make familiar with other options.*

# STEP3: Create an EC2 instance 

- Go to AWS EC2 console.
- First we need to create a security group it allows us to connect with SSH ``22 and allows TCP connection port on `8080`
- Go to `Security Groups` and create one with inboud rules allows to ssh `22` and custom tcp `8080`

![](/EC2/inbound%20rule.PNG)

- Go back to `Instances`
- Click `Launch intances` give a name you want.
- Choose Ubuntu AMI : `Ubuntu Server 20.04 LTS (HVM), SSD Volume Type` 

![](/EC2/Capture.PNG) 

- Instance Type: `t2.micro`
- Key Pair : You should have a key-pair on your local, if you don't have create one. I choose existing one `awssinem`. 

![](/EC2/KeYNAME.PNG)

- Leave all the rest of configuration as is.

#  STEP4: Connect to EC2 Instance via MobaXterm

- Copy the `Public IP` of your EC2-Instance.
- Go to your MobaXterm click `start local terminal` and session screen will be pop up.
- Go to first tab on the screen called `Session` and new screen will pop up
- Click the `SSH` 
- For 
- Remote Host : Paste your `Public IP`
- Specify username: `ubuntu` make sure you write ubuntu otherwise it will give `error`
- Click `Advanced SSH setting` and click `Use Private Key` and find your `key-pair` which you use for create your ec2 instance and upload your key to MobaXterm. And Click `OK`
- You can see following; 

![](./MobaXterm/moba2.png)

- You should see the connection is successfully achieved. 

![](./MobaXterm/moba3.PNG)

# STEP5: Configure Your Ec2 Instance


- We need to make sure our EC2 instance is currently fully updated.
- Before we run our codes following we need to change to root account. 

```bash
sudo su
```

- Output should look like this; 

![](./MobaXterm/moba4.PNG)

-We need to run following commands for making sure that all Ubuntu OS packages installed on the server are up to date. You can do this by running the following commands:

```bash
apt-get update -y
apt-get upgrade -y
```
- Now we need to upload the `java` to our machine and the version should match the java version of Maven Project that we created with `springboot`.

- Ubuntu 20.04’s default repository included Java 17. This is the easiest way to install the JDK using the apt package manager:

```bash
apt install openjdk-17-jdk openjdk-17-jre -y
```

- Once installed, verify the Java version using the following command:

```bash
java -version
```


- You should get the following output:

![](./MobaXterm/moba5.PNG)


- We need to upload  `Maven` as well.


```bash
apt-get install maven -y
```

- Check the version of maven

```bash
mvn -version
```

- Output should look like this;

![](/MobaXterm/moba6.PNG)



```bash
```



```bash
```


