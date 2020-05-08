Secret access key - n0ETlYp7lQyDzB+Dwi/XmwoSfCNVs8+JZxI754dE
Access key ID - AKIATOF753T27B3AAFFR
usr - scaling

====cmd as admin===
Microsoft Windows [Version 6.1.7601]
Copyright (c) 2009 Microsoft Corporation.  All rights reserved.

C:\Windows\system32>aws configure
AWS Access Key ID [None]: AKIATOF753T27B3AAFFR
AWS Secret Access Key [None]: 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
Default region name [None]: us-east-1
Default output format [None]:

C:\Windows\system32>
========

IAMRole-AutoScaling - IAM-Role Name



In userdata below script needs to be placed:
#!/bin/bash
yum install httpd -y
yum update -y
aws s3 cp s3://devopsenggr-feb-bucket /var/www/html/ --recursive
service httpd start
chkconfig httpd on

Makes sure you have a user fullaccess to EC2 
aws ec2 run-instances --image-id ami-xxxxxxxx --count 1 --instance-type t2.micro --key-name <<MyKeyPai>> --security-group-ids sg-xxxxxxxx -subnet-id subnet-xxxxxxxx

Create Instance - aws ec2 run-instances --image-id ami-0a887e401f7654935 --count 1 --instance-type t2.micro --key-name DevOps2020 --security-group-ids sg-0733a5e9452c7f415 --subnet-id subnet-fc2e8bb1
Name the instance - aws ec2 create-tags --resource i-instancename --tags Key=Name,Value=CLInstance


aws ec2 create-tags --resource i-051978004904f9417 --tags Key=Name,Value=CLInstance


=======GIT Command=====
[root@ip-172-31-95-254 demo]# history
    1  sudo yum install git -y
    2  git --version
    3  pwd
    4  mkdir demo
    5  cd demo/
    6  git init
    7  ls -a
    8  vi index.html
    9  git status
   10  git add index.html
   11  git status
   12  git commit -m "index.html commit"
   13  git status
   14  git log
   15  git log -oneline
   16  git log --oneline
   17  git show 57adad9
   18  date
   19  history
[root@ip-172-31-95-254 demo]#
===========

lambda stop fundtion in python:

import boto3
region = 'us-east-1'
instances = ['i-0b550a9aa28afe807']
ec2 = boto3.client('ec2', region_name=region)
def lambda_handler(event, context):
    ec2.stop_instances(InstanceIds=instances)
    print('stopped your instances: ' + str(instances))
	
lambda start fundtion in python:

import boto3
region = 'us-east-1'
instances = ['i-0b550a9aa28afe807']
ec2 = boto3.client('ec2', region_name=region)
def lambda_handler(event, context):
    ec2.start_instances(InstanceIds=instances)
    print('started your instances: ' + str(instances))

CLOUDWATCH > EVENTS > RULES
0 20 * * ? * STOP
0 10 * * ? * START

==================

pipeline
{
agent any
stages
{
	stage ('source code checkout')
{
		steps
{
			git branch: 'master', url: 'https://github.com/sijeshnambiar/maven-project'
}
}
	stage ('compile source code')
{
		steps
{
			withMaven(jdk: 'local_jdk', maven: 'local_mvn') 
{
				sh 'mvn compile'
}
}			
}
	stage ('test source code')
{
		steps
{
			withMaven(jdk: 'local_jdk', maven: 'local_mvn') 
{
				sh 'mvn test'
}
}			
}
	stage ('test source code')
{
		steps
{
			withMaven(jdk: 'local_jdk', maven: 'local_mvn') 
{
				sh 'mvn packgae'
}
}			
}
}
}
