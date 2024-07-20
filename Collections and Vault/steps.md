## Setup Ansible Collection and Vault

### Install Ansible

```sh
sudo apt update
sudo apt install ansible -y
```
### Install `boto3`

```sh
pip install boto3
```
### Install `amazon.aws` collection 

```sh
ansible-galaxy collection install amazon.aws
```
### Generate random password

Generate random password file using base64 encryption.

```sh
openssl rand -base64 2048 > vault-password
```

### Encrypt the variables file using the above password file

Execute the below command to encrypt the pass.yml file and write the key value pairs inside the pass.yml file

```sh
ansible-vault create variables.yml --vault-password-file <password-file>
```

### Create playbook

Create the play book by using variables in pass.yml

### Execute the playbook 

```sh
ansible-playbook  playbook.yml --vault-password-file <password-file>
```

