# jenkins-project
first  install jenkins in local computer or in an EC2 instance( better follow the official page for installation) then install sonar qube scanner plugin and activate it in tools.
create a node1 with ubuntu in ec2 instance in aws 
# create a node and install java in it
#sudo apt update
#sudo apt install openjdk-17-jre
#  in node_02 create a folder
$ mkdir jenkins-slave
$ cd jenkins_slave
$ chmod 755 jenkins_slave
# in jenkins-slave folder
$ ssh-keygen
$ cd ~
$ cd/root/.ssh
$ ls
it shows id_rsa ( private key) and id_rsa.pub (public key)
$ cat id_rsa
copy the key and go to credentials in manage jenkins 
select ssh 
as kind and then add private key
username:root
description: private-key
then click create
now goto nodes and cloud and click on new node
node name: Test-node
select permanent agent
number of executors: 3 
remote root dirctory : /home/ubuntu/jenkins-slave/
label: slave-2
# use this node with label expressions
launch method: launch via ssh
host: ip address of node1 ec2 instance
credentials: root(private-key) 
verification strategy : non verifying verification strategy
now click on save
# it shows test-node offline (error)
now go to mobaxterm terminal
$ cat id_rsa.pub
copy the public key
then
$ vi authorized_keys
paste the public key ans save it
now go to test node in nodes in manage jenkins
then click on bring this node  back online and click on launch agent
now node is connected
# install plugins
#install jdk (Eclipse Temurin installer)
#install docker ,docker pipeline ,docker-build-dtep,cloud bees docker build and publish
#install owaspdependency check
# goto tools to cofigure jdk ,maven,docker
# now create a free-style-job
# add git hub credentials by generating token in developer settings in github
# select 2 builds max in discard builds
# if you forgot jenkins username and password follow bellow steps
$ cd /var/lib/jenkins
$ ls
$ cp /var/lib/jenkins/config.xml /var/lib/jenkins/config.xml.back
$ ls
$ sudo vi /var/lib/jenkins/config.xml
$ In config.xml file <useSecurity>true</useSecurity> will be change with <useSecurity>false</useSecurity>
$ systemctl restart jenkins
$ sudo systemctl status jenkins
# now create a pipeline
new job named pipeline with template pipeline
# select hello world script
# use pipeline syntax if necessary










