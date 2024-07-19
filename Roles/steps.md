# Detailed Explanation of Creating and Pushing Ansible Roles

## **1. Create Role**
To start, create a new Ansible role. Ansible Galaxy provides a convenient command to initialize the structure of a new role.

```sh
ansible-galaxy init <role-name>
```
## 2. Split Tasks and Write All Tasks, Files, Variables, Handlers

Next, you will define the specific tasks your role will perform, as well as any variables, handlers, templates, and files it requires as mentioned in the repo.

## 3. Create Playbook by Mentioning Role
Once your role is defined, create a playbook that uses this role. Create inventory file with hostnames.
This playbook will apply the role to your target hosts.

## 4. Execute Playbook
Run the playbook to apply the role and deploy Apache on your target hosts.

```sh
ansible-playbook -i inventory playbook.yml
```
## 5. Access Website

After the playbook execution completes, verify that Apache has been installed and started by accessing the default Apache web page on your target hosts.

## 6. Push Role to GitHub

Next, push your role to a GitHub repository. First, initialize a Git repository in your role directory and commit your changes.
```sh
cd apache
git init
git add .
git commit -m "Initial commit of Apache role"
git remote add origin https://github.com/your_username/apache.git
git push -u origin main
```
## 7. Import role to Ansible-Galaxy

```sh
ansible-galaxy import <your_github_username> <your_repo_name> --token=<Ansible-Key>
```




