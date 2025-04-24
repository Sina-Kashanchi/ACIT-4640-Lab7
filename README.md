# 4640-w7-lab-start-w25

## Steps to complete the lab:
### Step 1: Create a new SSH key pair named "aws" and store it in the ~/.ssh directory
```
ssh-keygen -t rsa -b 4096 -f ~/.ssh/aws
```

### Step 2: Import the key to the AWS account using the "import_lab_key" script
```
./scripts/import_lab_key ~/.ssh/aws.pub
```

### Step 3: Run the terraform configuration to create 2 EC2 instances
```
cd terraform
terraform init
terraform apply
```

### Step 4: Edit the hosts.yml file
Add domain name, SSH username, and SSH private key file path for both servers

### Step 5: Complete the playbook
The following are the tasks completed in the playbook:
- Package module installs nginx
- File module creates the /web/html directory with permission 755
- Copy module copies the nginx config file to /etc/nginx/sites-available/default on the instances with permission 644
- File module creates a symbolic link from /etc/nginx/sites-available/default to /etc/nginx/sites-enabled/default
- Template module creates the index.html file from the index.html.j2 template and stores it in the /web/html directory on the instances
- Service module reloads the nginx service and ensures it starts automatically at boot

### Step 6: Run the playbook
```
ansible-playbook -i ansible/inventory/hosts.yml ansible/playbook.yml
```

### Step 7: Check if the html page can be rendered on http://<domain_name>
![image](./Lab7.png)
