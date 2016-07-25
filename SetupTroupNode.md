Set up a new troup node device
------------------------------

# Create ansible user account

Create the user account without shell (/bin/false), but create the home dir, so we can add the RSA keys later on:

```
sudo useradd -s /bin/false -m ansible
```

# Add the authorized keys

Log in with the newly created ansible account:

```
sudo su -s /bin/bash ansible
```
Then cd into the home directory and create a directory called ```.ssh```:

```
cd
mkdir .ssh
```

Create ```authorized_keys`` file:

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
