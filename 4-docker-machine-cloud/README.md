#Expose cointainer in cloud using docker-machine

`docker-machine` is a docker tool and is one of the docker mechanism to deploy containers to cloud providers

`docker-machine` uses "drivers" to deploy virtual instances in popular cloud providers. Every driver depends on a few configurations to work.

## Google Cloud driver

To create a compute instance(VM) in google cloud, we need to follow the `gcloud` tools [gcloud install process](https://cloud.google.com/sdk/downloads) for your OS, to deploy from your command line.

After the install process, we can use our google cloud account to create a new machine then connect to it and deploy containers. Let�s deploy our nginx site

```
$ gcloud auth login
$ docker-machine create -d google --google-project <cloud-project> <compute-name>
$ docker build -t mynginx .
$ docker run -d -p 80:80 mynginx

```

Now we can check if the cointainer is up go to <http://<google-compute-ip>>

Now let�s install aspnet service. Please go to the folder MyService inside this path

```
$ docker build -t aspservice .
$ docker run -it -p 5000:5000 aspservice
```
## Azure
docker-machine create -d azure --azure-ssh-user ops --azure-subscription-id <SubscriptionId> --azure-open-port 80 machine

## Amazon EC2 driver
To create an EC2 instance in AWS running Docker that we will later command from our local computer, we need the following variables set up : 

```
export AWS_ACCESS_KEY_ID=<your aws iam key>
export AWS_SECRET_ACCESS_KEY=<your aws iam key>

# According to when your AWS account was created, you may also need the following
export AWS_VPC_ID=vpc-xxxxxxxxx
export AWS_SUBNET_ID=subnet-xxxxxxxxx

```
$ docker-machine create -d amazonec2 aws01

Now you can deploy containers inside an Amazon�s virtual machine