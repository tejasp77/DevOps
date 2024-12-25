## Setup ansible host file and test connectivity

###  Setup Hosts file
Add this to file /root/hosts
```ini
[servers]
controlplane
node01
```
---
### Check functionality and connectivity
Executing ping module against both servers
```bash
ansible servers -i /root/hosts -m ping
```

Executing ping module against both servers and output to /root/ping_check
```bash
ansible servers -i /root/hosts -m ping > /root/ping_check
```
---
### Add to inventory for future environments
Update the /root/hosts file to have a test and prod environment
```ini
[servers]
controlplane
node01

[test_env]
controltest type=client
node01test  type=server

[prod_env]
controlprod type=client
node01prod  type=server

[non-prod:children]
servers
test_env
```

View the inventory with ansible-inventory to see the host groups
```bash
ansible-inventory -i /root/hosts --list
```

To see that in graph output use this command
```bash
ansible-inventory -i /root/hosts --graph
```

To see that in yaml output
```bash
ansible-inventory -i /root/hosts --list -y
```
---
