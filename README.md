# ansible-server-base

Sample Ansible playbook and role for setting up a Linux server with basic security.

## Setup

First install the necessary Python packages from the **requirements file**. 

```bash
pip install -r requirements.txt
```

Once complete, run the below command to install the **community general Ansible collection**.

```bash
ansible-galaxy collection install community.general
```

Lastly, the **sshpass** package is required for running the Ansible playbook. On **Linux distros** this is available as a package with the same name. To install on **MacOS** run the below command.

```bash
brew install esolitos/ipa/sshpass
```

Update the **inventory** file with your **SERVER_IP_HERE** and **LOCAL_PRIVATE_SSH_KEY_PATH** with your values.

## Assumptions

Currently the playbook makes the following assumptions:
1. That an ssh keypair is available at the location **~/.ssh** with the names **server_rsa** and **server_rsa.pub**.
   1. That you want to use the **server_rsa** as an authorized key for signing in to the non root account created.
2. That you want the below optional package(s) installed
   1. **openjdk-17-jdk-headless**
3. That you want the below optional port exposed
   1. **25565**

## How To Run

```bash
# Substitute PASSWORD_HERE with your desired user password then run in the project root directory
ansible-playbook -i inventory -u root -k \
--extra-vars user_password=PASSWORD_HERE server_playbook.yml
```

## To-Do List
1. Use role vars to abstract hardcoded values out of the role tasks
2. Abstract the packages installed for reusability
3. Abstract the ports exposed for reusability
