# Ansible Based deployment

Exercise scenario:

## Servers

You have have 3 linux servers:

1. server1, a management server
2. server2, a workload server
3. server3. a workload server

## Requirements

Using the method of your choice, create a system on the management server for modifying the workload servers and keeping them consistent. Your system must be able to do the following:

1. Read a list of users and create a user account for each
2. Distribute keys for these users
3. Install python 3.7 and the pandas module via pip
4. Copy over some (arbitrary) python code and execute it

Bonus if your system can create the workload servers and add a security group rule for port 22 as well, or say how this will be done.

Consider how your solution can be made extensible and later adapted to configure the servers, install software or even set-up an application.

## Assumptions

* All servers exist or are expect to exist in the same subnet

* All servers are running or are intended to run a RHEL-based Linux OS. For the purposes of demonstration we shall use CentOS.

* AWS credentials are provided either in the user's ".aws/credentials" file or exported as environment variables (AWS_ACCESS_KEY_ID and AWS_SECRET_ACCESS_KEY)

* A private key shall be provided for access to newly created EC2s

## Environment setup

To easily get the repo, first install git

```bash
yum install git
```

Before running any of the scripts present in this repo you should first install Ansible with the following command:

```bash
yum install ansible
```

It is also necessary to set up pip and boto on the management server

```bash
yum install python-pip
pip install boto3
```

As stated in the assumptions an AWS account credentials will have to added for instance setup steps

To ensure uninterupted running of scripts ignore host key checking by changing the following variable to False in 'etc/ansible/ansible.cfg'

```bash
[defaults]
host_key_checking = False
```