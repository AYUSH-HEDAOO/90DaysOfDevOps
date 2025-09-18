#### DOCKERFILE SYNTAX FOR MAKING CONTAINER AND RUN IT ###
#1.Base image syntax
FROM openjdk:17-jdk-alpine


#2.working directory for app
WORKDIR /app


#3.copy the code from your host to container (working directory)
copy src/Main.java /app/Main.java
copy src/quotes.txt /app/quotes.txt 
#or  we can write since the working directory is  already known. copy src/quotes.txt quotes.txt 
#if we want to copy all file the simply use "copy .."


#4. run the commands to install libraries or to compile code
RUN javac Main.java

#5.Expose the port
Expose 8000

#6.serve the app / keep it running
RUN ["java","Main"]


#### MAKING IMAGE from dockerfile###

 docker build -t(for tag) java-quotes(image name):latest(tag/verion) .(file path)

 if no match for platform  error ocurred here then  go to browser and serach "docker build --platform=" 
 now ise mai kisim bhi platform ki build bana sakta hu
 ex . for linux platform
 docker build -t java-quotes:latest --platform=linux/amd64

 ##check images /show images##
 docker images

#### RUN DOCKER CONTAINER ##

docker run -d -p 8000:8000 --name java-quotes-app java-quotes:latest


the do to instance and security group add inbound rule that is port 8000 and save 
then copy ip of instance  and go to browser paste it and write : 8000, you can access globaly
 # if a