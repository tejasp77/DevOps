## Install Ansible and verify functionality

### Install Ansible
```bash
apt -y install ansible
```

### Check ansible version
```bash
ansible --version
```

### Check ansible version and send to file
```bash
ansible --version >> /root/version
```

### Check ansible-doc help
```bash
ansible-doc --help
```

### Check all the modules and store them in a file /root/modules
```bash
ansible-doc -l | wc -l
ansible-doc -l | wc -l > /root/modules  
```

### Read the documentation on setup module
```bash
ansible-doc -s setup
```

### Read the documentation on copy module
```bash
ansible-doc -s copy
```

