![diemBox](https://github.com/xMeraki/COMP6905-Final/blob/master/screenshots/Picture1.jpg)

DiemBox Web Server Application
The First Caribbean Curated Subscription Box provider.

**Requirements**
- [Install aws cli globally](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-install.html)


**Instructions**

Clone this Repository

```Bash
$ git clone https://github.com/xMeraki/COMP6905-Final
```

Enter the folder
```Bash
$ cd COMP6905-Final
```

Create a new keypair Eg. Using the EC2 console

Place the keypair .pem file into the COMP6905-Final folder

Change the permission of the keypair
```Bash
$ chmod 400 <keypair file>
```

Next configure your aws information
```Bash
$ aws configure
```

Go into the fullstack.yml file and change the keypair to the name of your keypair and the ImageID to the image ID of the instaance you're using.

![Change](https://github.com/xMeraki/COMP6905-Final/blob/master/screenshots/change.jpg)



Run the Stack by running the command
```Bash
$ aws cloudformation create-stack --stack-name <name> -- template-body file://$PWD/fullstack.yml --parameters ParameterKey=NumberofAZs
```
You can check it being created on the CloudFormation Console

![Stack Deployed](https://github.com/xMeraki/COMP6905-Final/blob/master/screenshots/stackdeployed.jpeg)

Once the stack is deployed, copy the IP address from the EC2 instance 

Run the following:
```Bash
$ docker -H tcp://<your public ip>:2375 ps -a
```

To deploy the App to Docker:
```Bash
$ docker -H tcp://35.175.207.201:2375 ps -a
$ docker-compose -H tcp://35.175.207.201:2375 -f app.yml up -d
$ docker-compose -H tcp://35.175.207.201:2375 -f app.yml ps

```

After this is ran, you can check to see if everything works by going to
```Bash
http://<ec2 address>/
```


