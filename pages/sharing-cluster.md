---
title: Instructions for Sharing Clusters
#subtitle: By Riccardo Murri
author: Riccardo Murri
layout: page
hide: true
---

## Sharing access to a cluster

These instructions apply if you want to give other people access to an
existing cluster.  The person who sets up the cluster retains control of
the cluster: only this person can resize the cluster or stop/destroy it.

1. Collect SSH public keys from all the people you want to give access
to.  On MacOSX and Linux, SSH public keys are (usually) stored in a
file ending in `.pub` within the `.ssh` directory.

**Note:** SSH public key files should be text file consinting of a
single line, which must begin with the characters `ssh-`.  Invalid
SSH public key files can lock anyone of the cluster!

2. Use `elasticluster sftp` to upload all the SSH public key files to
the cluster front-end.  Each SSH public key should be stored in a
separate file.

3. Log in to the cluster, then run the following command for every SSH
public key file (replace `key.pub` with the actual path to the SSH
public key file)::

```
cat key.pub | tee -a $HOME/.ssh/authorized_keys
```

The above command will give another user access to the account you
are logging into on the cluster; you can apply the same procedure to
other accounts if you are running a multi-user cluster.


## Sharing control of a cluster

These instructions apply if you want to give other people control over
the cluster setup: those people will be able to resize, reconfigure, or
stop/destroy the cluster.  Sharing control of a cluster is a more
complicated and error-prone procedure than sharing *access* to a
cluster.

**Note:** Cluster control is separate from cluster access: this set of
instructions will allow other people to resize a cluster or destroy/stop
it -- but they will not give them the ability to log in to the cluster
via SSH.  Follow the instructions in the previous section to grant SSH
access to the cluster to other people.

1. All people wanting to share control of a cluster must already share
access to the same project / tenant / zone of the cloud where the
cluster is running.

2. All people wanting to share control of the cluster must share the
`[cluster/...]` section of the configuration file that was used as a
cluster template, and the `[cloud/...]`, `[login/...]`, and
`[setup/...]` sections referred to therein.  The easiest way to share
such configuration information is to move all these information into
a separate `.conf` file and copy it into your
`~/.elasticluster/config.d/` directory.

3. The person who created the cluster can now run this command to copy
the cluster state information into a `.zip` file::

```
elasticluster export -o /path/to/export/file.zip
```

4. Distribute the `.zip` file to other people who need to control the
cluster; they should copy it on the machines where they want to run
the `elasticluster` command.

5. Each person wanting to have control of the cluster size and lifecycle
can now run this command to import the cluster state::

```
elasticluster import /path/to/copied/export/file.zip
```

6. Everyone should now be able to see the cluster listed in the output
of `elasticluster list`.


[Go Back](advanced-cluster-setup)
