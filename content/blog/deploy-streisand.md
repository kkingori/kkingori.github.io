+++
date = "2016-05-10T17:04:50+03:00"
title = "Deploy streisand"

+++

Streisand sets up a new server running a wide variety of anti-censorship software that can completely mask and encrypt all of your Internet traffic. It also generates custom configuration instructions for all of these services. At the end of the run you are given an HTML file with instructions that can be shared with friends, family members, and fellow activists. 


### Install ansible

```
$ sudo apt-get install software-properties-common
$ sudo apt-add-repository ppa:ansible/ansible
$ sudo apt-get update
$ sudo apt-get install ansible

```

### Get Streisand

```
sudo apt-get install git

git clone https://github.com/jlund/streisand.git

cd streisand

```

Edit the inventory file and uncomment the final two lines. Replace the sample IP with the address (or addresses) of the servers you wish to configure. Don't put in localhost, the generated docs will be all wrong.

Edit playbooks/streisand.yml 

Change user from root to ubuntu ``` remote_user: ubuntu ```

just below that add ``` become: true ```

You're all set to build the streisand server on the host you have ssh'ed into. Just run

```
ansible-playbook playbooks/streisand.yml --connection=local
```

Wait for the setup to complete and look for the corresponding files in the 'generated-docs' folder in the Streisand repository directory. The HTML file will explain how to connect to the Gateway over SSL, or via the Tor hidden service. All instructions, files, mirrored clients, and keys for the new server can then be found on the Gateway. You are all done!

I normally use [Surge.sh](https://www.surge.sh) to access the generated docs.

### Install NodeJS

```
curl -sL https://deb.nodesource.com/setup_4.x | sudo -E bash -
sudo apt-get install -y nodejs
```

### Install Surge.sh

```
npm install --global surge
cd generated-docs
surge
```








