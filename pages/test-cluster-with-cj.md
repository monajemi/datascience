---
title: Test your cluster with CJ 
#subtitle: By Hatef Monajemi
author: Hatef Monajemi
layout: page
hide: true
---

* add your cluster info to `~/CJ_install/ssh_config`.  You may use the followng CJ commands to configure
or update your cluster.

```
cj config <CLUSTER_NAME>
cj config <CLUSTER_NAME> --update
cj config-update <CLUSTER_NAME>
```

Here is an example:    

```
[gce]
Host	        35.199.171.137
User            hatefmonajemi
Bqs             SLURM
Repo            /home/hatefmonajemi/CJRepo_Remote
MAT             ""
MATlib          ""
Python          python3.4
Pythonlib       pytorch:torchvision:cuda80:pandas:matplotlib:-c soumith
R               ""
Rlib            ""
[gce]

```
> note that `Host` is the IP address of your frontend node (e.g., `35.199.171.137`)


* go to `~/CJ_install/example/Python` and run `simpleExample` on your cluster:      

```
# update cj
cj update

# test CJ run
cj run simpleExample.py gce -m "Python on CPU test"
cj state
cj ls
```     
* go to `~/CJ_install/example/Python/pytorch/mnist` and run `mnist.py` on your cluster using GPU:   

```
cj run mnist.py gce -alloc "--gres=gpu:1" -m "Pytorch on GPU test"

# see state of your job
cj state

# see the run log
cj runlog 

# get a summary of all jobs on your cluster
cj summary gce
```

If everything makes sense, move on to running your own data science experiments.

[Go Back](elasticluster-clusterjob-model)
