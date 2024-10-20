## Terraform configuration directory
- main.tf - main configuration file containing resource directory
- variables.tf - contains variable declaration
- outputs.tf - contains outputs from resources
- providers.tf - contains provider definition

## Terraform commands

### terraform init
```bash
terraform init
```

### terraform plan
```bash
terraform plan
```

### terraform apply
```bash
terraform apply
```

### terraform show
The terraform show command prints out the current state of the infrastructure as seen by Terraform.
```bash
terraform show
```
Additionally, we can make use of the -JSON flag to print the contents in a JSON format.
```bash
terraform show -json
```

### terraform state show
This command prints out the current state of the infrastuucture resource as seen by terraform.
Syntax: terraform state show `<provider>_<type>.<resource>`
```bash
terraform state show local_file.file
```

### terraform output
If you want to print all output variables in the configuration directory, use the command terraform output.
```bash
terraform output
```
You can also print the value of a specific variable by appending the name of the variable to the end of the output command like this.
```bash
terraform output pet-name
```

### terraform validate 
To check syntax
```bash
terraform validate
```

### terraform fmt
This command scans the configuration files in the current working directory and formats the code into a canonical format.
This is a useful command to improve the readability of the Terraform configuration file.
```bash
terraform fmt
```

### terraform providers
To see a list of all providers used in the configuration directory, use the terraform providers command.
```bash
terraform providers
```
You can also make use of the mirror subcommand to copy provider plugins needed for the current configuration to another directory like this.
This command will mirror the provider configuration in a new path,
/root/terraform/new_local_file.
```bash
terraform providers mirror /root/terraform/new_local_file
```

### terraform refresh
The terraform refresh command is used to sync Terraform with the real-world infrastructure.

For example, if there are any changes made to a resource created by Terraform outside its control, such as a manual update, the terraform refresh command will pick it up and update the state file.
```bash
terraform refresh
```

This reconciliation is useful to determine what action to take during the next apply.

This command will not modify any infrastructure resource but it will modify the state file.

As we saw earlier, terraform refresh is also run automatically by commands such as terraform plan and terraform apply.
This is done prior to Terraform generating an execution plan.

This can however be bypassed by using the -refresh=false option with the command

### terraform graph
The terraform graph command is used to create a visual representation of the dependencies and a Terraform configuration or an execution plan.
```bash
terraform graph
```
To make more sense of this graph we can pass it through a graph visualization software such as Graphviz
```bash
apt update
apt install graphviz -y
```
Once installed, we can pass the output of the terraform graph to the DOT command which we installed using the Graphviz package, and generate a graphic.
```bash
terraform graph | dot -Tsvg > graph.svg
```
We can now open this file via a browser and it should show a dependency graph.


### terraform state

```bash
terraform state list
```

```bash
terraform state show <provider_resourcetype>.<resourcename>
```

```bash
terraform state mv source destination
```
```bash
terraform state mv <provider_resourcetype>.<resourcename1> <provider_resourcetype>.<resourcename2>
```
```bash
terraform state rm <provider_resourcetype>.<resourcename1>
```

Note: this will remove object from terraform management, it will apply infrastructure. terraform configuration files needs to be updated.
