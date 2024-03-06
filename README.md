# jenkins-project
first  install jenkins in local computer or in an EC2 instance then install sonar qube scanner plugin and activate it in tools.
create a node1 with ubuntu in ec2 instance in aws 
To install java
#sudo apt install openjdk-11-jre
create a folder
#mkdir jenkins_slave
#cd jenkins_slave
#chmod 755 jenkins_slave
in jenkins_slave folder
#ssh-keygen
#cd ~
#cd/root/.ssh
#ls
it shows id_rsa ( private key) and id_rsa.pub (public key)
#cat id_rsa
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
#use this node with label expressions
launch method: launch via ssh
host: ip address of node1 ec2 instance
credentials: root(private-key) 
verification strategy : non verifying verification strategy
now click on save
#it shows test-node offline (error)
now go to mobaxterm terminal
#cat id_rsa.pub
copy the public key
then
vi authorized_keys
paste the public key ans save it
now go to test node in nodes in manage jenkins
then click on bring this node  back online and click on launch agent







