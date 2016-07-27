Set up a new troup node device
------------------------------

# Create ansible user account

Create the user account with shell (/bin/bash) and create the home dir, so we can add the RSA keys later on:

```
sudo useradd -m ansible
```

# Add the authorized keys

Log in with the newly created ansible account:

```
sudo su ansible
```
Then cd into the home directory and create a directory called ```.ssh```:

```
cd
mkdir .ssh
```

Create ```authorized_keys``` file:

```
touch .ssh/authorized_keys
```

Open the authorized key file and paste the content of ```id_rsa.pub``` from your ansible control master server (file is usually under ```~/.ssh/id_rsa.pub```.

```
nano .ssh/authorized_keys
```

The content of the file will look something like this:
```
ssh-rsa AAAA...<large base64 encoded string>...Od ansible@vm-cm-master-0
```

To test the setup, login to your Ansible control server and try to ssh to the device node using the ```ansible``` account:

```
user@vm-cm-master-0$ sudo su -s /bin/bash ansible
ansible@vm-cm-master-0$ ssh node-device.localcluser.lan 
```

If there are no errors, then you have correct set up (You may see some message from the node and then ``Connection to node-device.localcluster.lan closed.`` -  this is fine because we have set up /bin/false as shell for ``ansible`` account on the node). 
