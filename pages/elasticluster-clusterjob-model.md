---
title: ElastiCluster-ClusterJob Computing Model 
#subtitle: By Hatef Monajemi
author: Hatef Monajemi
layout: page
hide: true
---


# Introduction
This is a supplemetary page to the paper "Painless Computing Platform for Ambitious Data Science" by Monajemi et al. Here you will learn how to conduct massive computational experiments in the cloud using an approach developed by Hatef Monajemi and Riccardo Murri during the first iteration of [Stats285 course](https://stats285.github.io) at Stanford University in the Fall of 2017; You will use [elasticluster](https://gc3-uzh-ch.github.io/elasticluster/) to build your **own personal cluster** in the cloud 
and then use [clusterjob](http://clusterjob.org) (CJ) to run jobs on this cluster. Both of these steps are very straight-forward and painless.    
    This documents contains the detail of setting up your (GPU-accelerated) cluster and testing that it works properly with CJ. Once these steps are completed, you can then enjoy conducting your own massive data science experiments in the cloud painlessly.


# Questions and Comments 
Please send your questions to [CJ's Google group](https://groups.google.com/forum/#!forum/clusterjob). For other inquires, please send an email to [hatefmonajemi@gmail.com](mailto:hatefmonajemi@gmail.com) or [riccardo.murri@gmail.com](mailto:riccardo.murri@gmail.com)

# Building your cluster in the cloud

To create your own cluster in the cloud, you should take the following 4 steps:

1. [Install ClusterJob](#part-1-install-cj)
1. [Setup your cloud account](#part-2-setup-your-cloud-account)      
1. [Create your cluster using 0-install ElastiCluster script](#part-3-create-your-cluster-using-elasticluster)
1. [Test your cluster works with CJ](#part-4-test-your-cluster-works-with-cj)

## Part-1: Install ClusterJob

- Sign up for ClusterJob on [clusterjob.org](http://clusterjob.org)   
- Follow [CJ Installation Guide](http://clusterjob.org/documentation/book.html#_step_2_installing_cj) to install it on your machine.



## Part-2: Setup Your Cloud Account
- [Setup instructions for Google Compute Engine](./gce-setup-instructions)
- [Setup instructions for Amazon EC2](./aws-setup-instructions)
- [Setup instructions for Microsoft Azure](./azure-setup-instructions)


## Part-3: Create Your Cluster Using Elasticluster

1. Get elasticluster 0-install script from GitHub or [download it from this website](../assets/files/elasticluster.sh)   
```
curl -O https://raw.githubusercontent.com/gc3-uzh-ch/elasticluster/master/elasticluster.sh
chmod +x elasticluster.sh
```
2. Provide your desired configuration
```
    elasticluster.sh list-templates
    vim ~/.elasticluster/config
```    
    You may use the default Elasticluster config template or [`elasticluster_config` that is provided with this companion page]({{site.url}}/datascience/assets/files/elasticluster_config.txt). You can get `elasticluster_config` via the following commands:
    ```
    curl -O  https://monajemi.github.io/datascience/assets/files/elasticluster_config
    cp elasticluster_config ~/.elasticluster/config
    ``` 
    
    You must change the contents of the elasticluster config file `~/.elasticluster/config` to reflect your own credentials and choice of resources.  As an example, on Google Cloud, you should retrive your `project_id`, `client_id`, and `client_secret` by visiting the [Credential Page](https://accounts.google.com/signin/v2/sl/pwd?service=cloudconsole&passive=1209600&osid=1&continue=https%3A%2F%2Fconsole.cloud.google.com%2Fproject%2F_%2Fapiui%2Fcredential&followup=https%3A%2F%2Fconsole.cloud.google.com%2Fproject%2F_%2Fapiui%2Fcredential&flowName=GlifWebSignIn&flowEntry=ServiceLogin) and update the contents of `~/.elasticluster/config` by providing these credentials.

    [See config example on GitHub](https://github.com/monajemi/datascience/blob/master/assets/files/elasticluster_config.txt)

    > [`gcloud`](https://cloud.google.com/sdk/gcloud/) provides useful commands to see the available options, for example:   
    > `gcloud compute machine-types list --zones us-west1-a`    
    > lists all the machine types that are availbale in zone us-west1-a     
    > This infomation can be found online on [Google](https://cloud.google.com/compute/docs/machine-types)   
    > Also,  `gcloud compute images list` list all the available images.

<a href="./advanced-cluster-setup"><span style="background-color: #FFFF00">Advanced Tips</span></a	>   

3. Spin up your cluster 
```
./elasticluster.sh -vvvv start gce
```    
> Note that cluster named `gce` is fully defined in your `~/.elasticluster/config`. For convenient use, you may add an alias 
> to your `~/.bashrc` or `~/.bash_profile`:     
> `alias elasticluster='/PATH/TO/SCRIPT/./elasticluster.sh'`

	if you run into error, and asked to run the setup again, do so using       
    ```bash
    elasticluster -vvvv setup gce
    ```    

* You can also monitor the progress at your cloud console ( e.g., [Google Cloud Consol](https://console.cloud.google.com/) , [EC2 Consol](http://console.aws.amazon. )   
	   
    **if everything goes well, you will see** `your cluster is ready!`. **This is the moment you should shout** *Yay!* **and congratulate yourself. You now have your own cluster!**
	

* Get the IP address of the `frontend` node using:
    ```
    elasticluster list-nodes gce
    ```    
	example: `35.199.171.137`

* Login to your cluster to test it   
    ```
	ssh <USERNAME>@<FRONTEND_IP>
	```    
	example: `ssh hatefmonajemi@35.199.171.137` (for GCP, your gmail ID is your username)
	
* To destroy your cluster:
    ```bash
    elasticluster -vvvv stop gce
    ```
<span style="color:red"> Note that this command will destroy your cluster and you lose all the data on it. Make sure you get your data to a safe storage place before you destroy your cluster. </span>  

[comment]: # ( You can shut-off your cluster and reinitiate at a later time by logging to your [consol](https://console.cloud.google.com/). Currently ElastiCluster does not have this capability. For more info please visit [stopping-or-deleting-an-instance](https://cloud.google.com/compute/docs/instances/stopping-or-deleting-an-instance) )       

## Part-4: Test your cluster works with CJ

After you have launched your cluster successfully, it is time to test it by running a sample job on it
using **ClusterJob**. Follow the instructions on [Test Your Cluster With CJ](./test-cluster-with-cj).


