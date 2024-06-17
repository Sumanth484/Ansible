# Ansible
Repo gives brief info on how to use Ansible for configuration management

# Getting Started with Ansible

If you are just starting with Ansible, follow the steps below to get started.

## Step 1: Setup EC2 Instances

1. Create one EC2 instance and name it `Ansible_Server`.
2. Create two more EC2 instances and name them `Target_Server1` and `Target_Server2`.

## Step 2: Install Ansible

1. Login to `Ansible_Server` via SSH or Session Manager and execute the following commands:

    ```bash
    sudo apt update
    sudo apt install ansible -y
    ```

2. Verify whether Ansible is installed by running the command:

    ```bash
    ansible --version
    ```

## Step 3: Enable Passwordless Authentication

1. **Generate Public and Private Key on `Ansible_Server`**:

    ```bash
    ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
    ```

    Follow the instructions and press enter to generate the key in the default path.

2. **Copy the Public Key to Target Servers**:

    ```bash
    ssh-copy-id -i ~/.ssh/id_rsa.pub -o "IdentitiesOnly=yes" -i /path/to/your.pem ubuntu@target_server1_ip
    ssh-copy-id -i ~/.ssh/id_rsa.pub -o "IdentitiesOnly=yes" -i /path/to/your.pem ubuntu@target_server2_ip
    ```

3. **Verify SSH Access to Target Servers**:

    ```bash
    ssh ubuntu@target_server1_ip
    ssh ubuntu@target_server2_ip
    ```

## Step 4: Create an Inventory File

Create an inventory file and enter the Target Servers' IP addresses using the command:

```bash
vim inventory
```

## Step 5: Run Ansible Ad-Hoc Command

Run the following Ansible ad-hoc command to create files on the Target Servers:

```bash
ansible -i inventory all -m "shell" -a "touch /tmp/sample"
```

Now you can verify whether the files are created on the Target Servers or not.

