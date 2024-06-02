# HELM Commands

## HELM repo commands

To list chart repositories

```bash
helm repo list
```

To add a chart repository

```bash
helm repo add bitnami https://charts.bitnami.com/bitnami
helm repo add brigade https://brigadecore.github.io/charts
```

To remove chart repository

```bash
helm repo remove brigade
```

## HELM search commands

To search for keyword in charts

```bash
helm search repo mysql
helm search repo nginx
helm search repo nginx –versions
```

To search for charts in the Artifact Hub or your own hub instance - [artifacthub.io](https://artifacthub.io/)

```bash
helm search hub nginx
```

To verify how many charts available on the hub for nginx in the Artifact Hub or your own hub instance - [artifacthub.io](https://artifacthub.io/)

```bash
helm search hub nginx | wc -l
```

## HELM install, updrade and delete commnds

To install helm chart deployment

```bash
helm install my-mariadb bitnami/mariadb --version 18.2.0
```

Note: As per the release workflow, we are already aware Helm Don't wait for the successful installation of the Kubernetes resources. It will simply submit the validated YAML to the community's cluster and exit out with the success status.

To install hel chart deployment using user supplied SET parameter

```chart
helm install my-mariadb --set auth.rootPassword=secretpassword,auth.database=app_database bitnami/mariadb --version 18.2.0
```

To install helm chart deployment using user supplied values yaml file

```bash
helm install -n database --values db-values.yml my-mariadb bitnami/mariadb --version 18.2.0
```

To render chart templates locally and display the output.

```bash
helm template -n database --values db-values.yml my-mariadb bitnami/mariadb --version 18.2.0
```

**Important Note:** Using the `helm template` command, we can generate the HTML files which are directly deployable with the Kubernetes. And there is a one benefit with the helm template command to execute the helm template command, the working Kubernetes cluster is not required. It will not validate those YAML files against the Kubernetes. So Kubernetes is installed or not. If we just have the helm install on your machine, we can generate those YAML files with the helm, we can generate the YAML files for any object eg, Redis Rabbit, Kafka Air flow, Tomcat engine, etc. There could be the number of software which are very popular and if we want the all working YAML file for the softwares, we can simply generate them with the help of helm template Command and the Kubernetes working configuration is also not required to execute this command and generate these YAML files. So this is the way we can generate the YAML files with the help of a helm template command.

To wait for the successful installation of your pod

```bash
helm install my-mysql bitnami/mysql --version 11.1.0 --wait
```

**Note:** if flag --wait set, will wait until all Pods, PVCs, Services, and minimum number of Pods of a Deployment, StatefulSet, or ReplicaSet are in a ready state before marking the release as successful. It will wait for as long as --timeout

Add timeout to wait for any individual Kubernetes operation (like Jobs for hooks) (default 5m0s)

```bash
helm install my-mysql bitnami/mysql --version 11.1.0 --wait --timeout 20m
helm list
```

**Note:** if you want to override the timeout, you can override the timeout by a flag timeout and define timeout limit. Default timeout is 5mins

**Important Note:** Definitely recommend to use the custom timeout whenever we are using the wait with helm, because whenever we are using such installation with the CD pipeline, the wait is must we see that are getting the deployed. 

To upgrade helm chart deployment 

```bash
helm upgrade -n database --values db-values.yml my-mariadb bitnami/mariadb --version 18.2.0
```

To upgrade helm chart deployment with --wait and --timeout flag

```bash
helm upgrade my-mysql bitnami/mysql --version 11.0.0 --wait --timeout 20m
kubectl get pods
helm list -A
```

**Upgrade Scenario:** While doing the upgrade, there could be a number of scenario. Let's suppose you are upgrading your release with some random value or with some incorrect value. So we will execute the my SQL upgrade and let's suppose we are upgrading it with some incorrect value. So let's suppose we are using set flag and we are using image dot pull policy right in the k8s. We have the image policy. The default value could be the always or never. Let's suppose we are providing some incorrect value. Like my name, we are providing the image pool policy value my name.

```bash
helm upgrade my-mysql bitnami/mysql --version 11.0.0 --set image.pullPolicy='anshul' --wait --timeout 20m
```
Due to this, helm command is not returning anything. It is not returning anything because this is not the correct policy. And if we are using the wait with this policy because this is not the correct policy. So what will happen by default? It will wait for 20 minute and that is definitely not a good thing. So what we will do, we will press control C to exit out from this command and execute the helm list again. 
Deployment is status is failed, although the deployment status is failed. But we are using wait with a timeout so it is not able to reply the command. So my deployment will not come in the successor state. It will wait for the default timeout until the deployment is status will be success. This could be the problem with the upgrade.
So what could be the solution?
use --atomic flag while upgrade

if set, the installation process deletes the installation on failure. The --wait flag will be set automatically if --atomic is used

```bash
helm upgrade my-mysql bitnami/mysql --version 11.0.0 --set image.pullPolicy='anshul' --atomic
helm history my-mysql
```
Basically the application of atomic is whenever you are upgrading your helm deployment, if your deployment is not coming up with the latest version by which you are upgrading it, then Helm will automatically roll back your deployment to the previous version, which was running successfully. So in this case, once I will execute this command because I'm providing the incorrect value. So this will not come up successfully. This upgrade will fail. So what Helm will do?
Helm will roll out my complete deployment to the previously successfully state, which was revision number two. So whenever you want such kind of performance, such kind of setting in your product, that if we are upgrading your production grid system and we want that if upgrade will not go successful, then helm should automatically roll back my deployment to the previously successfully state. Then we need to use the atomic.
We don't need to specify the weight with the atomic. It is in-built with the atomic command. If we want, we can specify the timeout.

![image](https://github.com/tejasp77/DevOps/assets/165159032/77caa6e0-ec6e-45ea-9db1-d29163f7c02d)

To delete the deployment using helm in default namespace

```bash
helm delete my-redis
```

To delete the deployment using helm in specified namespace

```bash
helm delete my-redis -n redis
```

To uninstall a release in specified namespace

```bash
helm uninstall my-mariadb -n database
```

**Note:** This command takes a release name and uninstalls the release. It removes all of the resources associated with the last release of the chart as well as the release history, freeing it up for future use.
Use the `--dry-run` flag to see which releases will be uninstalled without actually uninstalling them.

```bash
helm uninstall my-mariadb -n database --dry-run
```

To uninstall release keeping history and secrets

```bash
helm uninstall my-mariadb -n database --keep-history
```

**Note:** After running `--keep-history` flag in helm uninstall command, we can verify k8s secrets and helm history command check if revision history persists.
If we will delete any of these secret explicitly, the revision history will also be deleted because Helm is reading all this data from these secrets.

```bash
kubectl get secrets -n database
helm history my-mariadb -n database
```

To reinstall it and you want to reinstall it with some specific revision

```bash
helm rollback my-mariadb 3 -n database
```

**Note:** After rollbacks successful, we can check with `helm list`, `helm history` command to get new revison number and also the secrets with new revision number using `kubectl get secrets` command

```bash
helm list -A
helm history my-mariadb -n database
kubectl get secrets -n database
helm get values my-mariadb -n database --revision 5
```

**Imp Note:** We can realize that how powerful the helm is and how important this is to keep the history of your deployments. Because if we have the history of our deployment, Helm can rollback our application from any state. It doesn't matter that it's being destroyed, deleted, halted. Helm can restore your application from any specified release if the release history is available with the helm. So that is the power of helm and that is the power of keeping the deployment. History is specifically for the production services.

## Kubectl list pods 

To list all running pods

```bash
kubectl get pods -A
```

To delete running pod

```bash
kubectl delete pod redis-client
```
## HELM deployment release history details commands

To show the status of a named release

```bash
helm status my-mariadb -n database
```

To get information about the helm deployment

```bash
helm list -A
```

To lists all of the releases for a specified namespace

```bash
helm list
```

To lists all of the releases for a all other namespace including specified namespace

```
helm list --all-namespaces
```

To get more details of deployment for example release notes

```bash
helm get notes my-mariadb -n database
```

To get details of user supplied values which were were provided to helm deployment

```bash
helm get values my-mariadb -n database
```

To fetch the user supplied values of individual revisons deployed by helm

```bash
helm get values my-mariadb -n database --revision 1
```

**Notes:** helm stores the secret for each revision of your deployment and in the secret it have the complete details of your deployment. So, these values are fetching for this particular revision from these particular secrets.

To know the all values which is being supplied to your deployment.

```bash
helm get manifest my-mariadb -n database --revision 1
```

To fetch release history

```bash
helm history my-mariadb -n database
```

To roll back a release to a previous revision

```bash
helm rollback my-mariadb 1 -n database
```

To verify what resources will be created before before helm deployment use `--dry-run`

```bash
helm install -n database --values db-values.yml my-mariadb bitnami/mariadb --version 18.2.0 --dry-run
```

To verify in debug mode what resources will be created before before helm deployment use `--dry-run` along with `--debug`

```bash
helm install -n database --values db-values.yml my-mariadb bitnami/mariadb --version 18.2.0 --dry-run --debug
```

**Note:** Using --dry-run command it is shows k8s yaml files which we see in the output of the command. for example, yaml file for secrets, services, etc.

To generate k8s resources YAML file before deployment use `helm template` command

```bash
helm template -n database --values db-values.yml my-mariadb bitnami/mariadb --version 18.2.0
```

To view the k8s secret details in yaml format

```bash
kubectl get secrets -n database sh.helm.release.v1.my-mariadb.v1 -o yaml
```

**Note:** K8s secret contain the information in the encoded format. We can decode it, there are multiple commands available on the Internet to decode the Kubernetes secrets.

## Create your own helm chart

Create github repository to push your custom helm chart

To create a new chart with the given name

```bash
helm create foo
```

This command creates a chart directory along with the common files and directories used in a chart.

For example, `helm create foo` will create a directory structure that looks something like this:

```
foo/
├── .helmignore   # Contains patterns to ignore when packaging Helm charts.
├── Chart.yaml    # Information about your chart
├── values.yaml   # The default values for your templates
├── charts/       # Charts that this chart depends on
└── templates/    # The template files
    └── tests/    # The test files
```
![image](https://github.com/tejasp77/DevOps/assets/165159032/413a0097-fc04-4913-8df7-03d6dbf81b54)

**Note:** While creating folder for custom chart, _ is not allowed. hyphen - is allowed

To install custom helm chart

```bash
helm install custom-deployment my-first-chart/
```
![image](https://github.com/tejasp77/DevOps/assets/165159032/a9639326-9e02-4ecd-ae4b-e2712b1c1655)

Note: While creating custom helm chart, by default it will take the nginx template. So actually it is deploying the engine x container within your custom deployment or within the pod of your custom deployment. 

![image](https://github.com/tejasp77/DevOps/assets/165159032/89b6a150-e7b3-4b92-a935-7d2ee2b843c0)

Note: If we look at the k8s resources generated by our custom helm chart, by default it has created 4 k8s resources object - deployment, replicaset, service and pod. 

Make changes in chart.yml and values.yml file

Added keywords element and updated chart version to 1.0.0

![image](https://github.com/tejasp77/DevOps/assets/165159032/fd22feb5-f29a-4b1f-9e29-61ff4032ed5e)

Updated replicaset value from 1 to 3

![image](https://github.com/tejasp77/DevOps/assets/165159032/b048d01f-2d18-48c9-b378-b1c39b29f753)

**Chart.yaml will contain the metadata of your helm chart where we will mention the application version, the type of the application, the chart version, etc. There are a number of things which we can define in the metadata.** 

**Note:** Other k8s resources hpa.yaml, ingress.yaml, serviceaccount.yaml which are inside templates folder are not created by default because these YAML files are conditional based resources. If we passed parameters from values.yaml with enabled value then only this particular resources will be deployed.

**Deployment YAML is the main file of the chart which will deploy all the resources this deployment.**

**Templates folder contains the YAML files, the definition of the resources which will be deployed on the Kubernetes cluster.**

**helper.tpl file contains the functions with the go template language syntax.** So whenever we will initiate our chart from this particular helper file, this function will be called and It will generate the name and it will supply the name to your deployment eg. deployment.apps/`custom-deployment-my-first-chart` This name is basically being constructed by this function. So, helpers will contain the functions and using these functions we can generate the values within our YAML for the Kubernetes. WE can create the function in the go template language syntax, and these functions will be used by our YAML file to generate the final deployable YAML on the Kubernetes, which will deploy the Kubernetes resources.

To render chart templates locally and display the output



To package a chart directory into a chart archive

```bash
helm package my-first-chart/
helm package my-first-chart/ -d /root/
```

![image](https://github.com/tejasp77/DevOps/assets/165159032/cffe6bce-dc06-411a-87e8-3bebce260dd2)

**Note:** This command packages a chart into a versioned chart archive file. If a path is given, this will look at that path for a chart (which must contain a Chart.yaml file) and then package that directory. Versioned chart archives are used by Helm package repositories. It creates naming convention with chart name and chart version with tar and zip file.
this package will be deployable on all the environment without any dependency either that is a development, production, staging or any other regression environment. So using this way we can package our chart.

To examine a chart for possible issues. 

```bash
helm lint my-first-chart/
```

![image](https://github.com/tejasp77/DevOps/assets/165159032/15158a4b-2004-4632-aa1e-0f015d0fa4a3)

This command takes a path to a chart and runs a series of tests to verify that the chart is well-formed.

**Note:** `helm lint` helps to validate our helm chart while we are preparing our custom helm charts.

To render chart templates locally and display the output.

```bash
helm template my-first-chart
```

**Curly brackets are the actions in the template, whatever the content you are getting within the YAML file. The template actions is a dynamic information and that information needs to be resolved at a runtime.**

`{{ "Hi We are learning" }} {{ "HELM" }}`

It is starting here and ending here, starting here and ending here. That content is a dynamic content which will be resolved at a runtime. So, curly brackets are called the template actions. We will see this helpers.tpl and also k8s manifest files in templates folder. So within the templates in a helm mostly you will be using the loops, variables, conditions and that content is basically covered with the curly brackets `{{ }}` like this.

Make changes in deployment.yaml file to add template actions

![image](https://github.com/tejasp77/DevOps/assets/165159032/fe86c353-1d03-4826-9390-fad5e0f176ea)

Run the helm template command to generate k8s template locally

```bash
helm template my-first-chart
```

![image](https://github.com/tejasp77/DevOps/assets/165159032/8c84e6f6-816f-4b1f-bc59-4fec77e36402)

In order to access information in template,  we can simply call . which is call period inside curly brackets followed by yaml file name eg. `{{ .Values.replicaCount }}`

Make change in deployment.yaml file 

![image](https://github.com/tejasp77/DevOps/assets/165159032/aeb3db77-eee7-4a3e-8e2c-14f6efe5ef24)

Run helm template command to generate k8s template locally

```bash
helm template my-first-chart
```

![image](https://github.com/tejasp77/DevOps/assets/165159032/94257ad3-d9cc-45d4-b463-44f37efdb274)

---

**Pipe function template**

- This pipe function `|` will chain these functions or data and it will supply the first function output as the input to the next
  function. The particular function will generate some input and if we are putting pipe after this and putting another function,
  then the output of this function will be supplied as the input to this function.

  Added customblock in values.yml file. Keep email element as blank.
    
  ![image](https://github.com/tejasp77/DevOps/assets/165159032/caa0783d-f4af-472c-8b3a-1cec3503ad23)

  Added template action to access customblock from values.yml file
    
  ![image](https://github.com/tejasp77/DevOps/assets/165159032/69923f25-6a94-4d1f-aca6-da7821cdd166)
    
  Run the helm template command and check the deployment.yml file
    
  ![image](https://github.com/tejasp77/DevOps/assets/165159032/757472fd-4e97-46f2-8eef-7f08539be1c9)
    
  We are getting the output with pipe functions.

---

**nindent function template**

-  This function basically provide a new line and indentation of defined argument. When we are defining an indent for it means
   new line indentation with for space, new line indentation. For example, `nindent 4` this will provide new line indentation
   with 4 spaces.

   Make changes in deployment.yml by adding nindent function

   ![image](https://github.com/tejasp77/DevOps/assets/165159032/89dc9e5e-9acf-4181-9ee8-9b9ca4f0eb5a)

   Run the helm template command and check the deployment.yml file

   ![image](https://github.com/tejasp77/DevOps/assets/165159032/73cc4a2f-9430-41df-a633-394b16452326)

   We are getting output with indendation function.
   
---
**if conditional logic in template**

Make changes in values.yml. Keep name element as boolean value.

![image](https://github.com/tejasp77/DevOps/assets/165159032/f2f46ede-b1ee-4f82-9c66-82f9769a3a2e)

Make changes in deployment.yml file by adding if contion 

![image](https://github.com/tejasp77/DevOps/assets/165159032/63da96cb-70d9-45e2-9c71-942fa73faa4f)

Run the helm template command and check the deployment.yml 

![image](https://github.com/tejasp77/DevOps/assets/165159032/acc39c59-09bf-4827-b7ca-67baee853e71)

Getting if condition output as expected with true value.

Edit the values.yml file and set to false

![image](https://github.com/tejasp77/DevOps/assets/165159032/10309ac2-9f5e-463b-9fe5-83a9d378a6d8)

Run the helm template command and check the deployment.yml 

![image](https://github.com/tejasp77/DevOps/assets/165159032/5e36efac-6682-4b12-a51b-c923ea3d45f9)

Getting if condition output as expected with false value.

Edit the values.yml file and add the else condition.

![image](https://github.com/tejasp77/DevOps/assets/165159032/c1718a2b-d469-4d4a-a286-c0c2ecc4e168)

Run the helm template command and check the deployment.yml 

![image](https://github.com/tejasp77/DevOps/assets/165159032/4c9b2e14-d304-428e-9c65-f164820ff3ae)

Getting  if condition output as expected with false value

---

**Typecast values to YAML template using with function**

Edit the values.yaml file and add list of names

![image](https://github.com/tejasp77/DevOps/assets/165159032/033392ce-68c0-412f-b6e8-ab84303f9490)

Edit the deployment.yml file and add the with function with typecast toYaml in template action code block.

![image](https://github.com/tejasp77/DevOps/assets/165159032/a7386736-6d9d-46e1-9ed4-0546daa7c312)

Run the helm template commands and check the deployment.yml 

![image](https://github.com/tejasp77/DevOps/assets/165159032/69d8bb01-0d81-4123-8789-f1d2180ef270)

Getting the expected output using with function.

Edit the values.yml file and keep name element as empty array

![image](https://github.com/tejasp77/DevOps/assets/165159032/a511d1cb-f407-4eb4-a1f8-7acf0b8d2f44)

Edit the deployment.yml and add the author element and else condition in template action code block.

![image](https://github.com/tejasp77/DevOps/assets/165159032/873ba516-c242-4076-afcc-eb1abc717b24)

Run the helm template and check

![image](https://github.com/tejasp77/DevOps/assets/165159032/11ac33db-0381-4a1c-afbd-2eea365351d6)

Getting expected output.

---

**Variables in templates**

Edit deployment.yml file and add the variable and pass in if condtion within template action. 

![image](https://github.com/tejasp77/DevOps/assets/165159032/5ea3a642-b20a-4c37-92e0-e4db8896a49e)

Run the helm template command and check

![image](https://github.com/tejasp77/DevOps/assets/165159032/5fb41206-ec83-4c33-b9d3-fe47e368535f)

Getting output as expected.

View the values.yml and use autoscaling element

![image](https://github.com/tejasp77/DevOps/assets/165159032/47d88a1d-ae24-4855-b8a3-bb031bb5658d)

Edit the deployment.yml and replace the variable value with autoscaling value.

![image](https://github.com/tejasp77/DevOps/assets/165159032/cd8f8f60-5215-4ee8-9dfe-710b3f430dc4)

Run the helm template command and check

![image](https://github.com/tejasp77/DevOps/assets/165159032/f137fa0c-17b3-4e26-bb04-bd4c155746d0)

Getting output as expected.

---
**Loops in template**

Edit the deployment.yml file and add the range iteration

![image](https://github.com/tejasp77/DevOps/assets/165159032/7b4bc713-f9ca-40d4-9e97-1dbf3d9c4531)

Run the helm template command and check

![image](https://github.com/tejasp77/DevOps/assets/165159032/af77b5d9-72f1-4b4b-bc45-357332f98ce4)

Getting expected output.

View the values.yml and use the image dictionary element

![image](https://github.com/tejasp77/DevOps/assets/165159032/c8e6df9d-92c5-49d5-8780-9086fcdb3716)

Edit the deployment.yml file and add the key value in 3rd range iteration

![image](https://github.com/tejasp77/DevOps/assets/165159032/67cb4070-cab4-4a65-8ac8-8251ae48f4a5)

Run the deployment.yml file and check

![image](https://github.com/tejasp77/DevOps/assets/165159032/5cbaff72-3b1c-453f-8ab3-f0213bd315f5)

Getting expected output.

---

**Template Validation Commands**

- If we have some syntactical error in templates that could be identified using the `helm lint` and `helm template` command.

- `helm install` using `--dry-run` command validates the object, the YAML object with the Kubernetes that that particular object is a deployable or not. In addtion to this it also validates syntactical error in templates.

![image](https://github.com/tejasp77/DevOps/assets/165159032/249f49fc-2351-4cfe-b626-d8ed8f5564d5)

---

**Chart Dependencies**

The the use case is whenever we are deploying the web application with the helm chart, the backend application should also get deployed. This can be done using chart dependency. 

For example, we are working on the web application chart, but web application chart itself dependent on the backend chart. So, in our web application chart and in the dependency, we will mention the back end chart. To add dependencies in helm chart, we need add dependencies element in Chart.yml file.

Edit the chart.yaml and the depenedencies element. For two backend applications with mysql and rabbitmq.

![image](https://github.com/tejasp77/DevOps/assets/165159032/f4db9da0-28de-412d-bdac-bff28bcb0960)

To update charts/ based on the contents of Chart.yaml

```bash
helm dependency update my-first-chart
```

This command verifies that the required charts, as expressed in 'Chart.yaml', are present in 'charts/' and are at an acceptable version. It will pull down the latest charts that satisfy the dependencies, and clean up old dependencies.

![image](https://github.com/tejasp77/DevOps/assets/165159032/ec009a1e-4f49-4f39-b745-da68bd1557d0)

Run the helm install command 

![image](https://github.com/tejasp77/DevOps/assets/165159032/7e706f1c-7315-4339-a1a6-d66f62182fde)

Run the kubectl get pods command

![image](https://github.com/tejasp77/DevOps/assets/165159032/755a2a0f-8ec5-4197-82e4-01902ead717a)

We can see dependencies are installed.

**Conditional Chart Dependencies**

Edit Chart.yml and add the condition for msql element

![image](https://github.com/tejasp77/DevOps/assets/165159032/31ed81ac-1434-4165-bd90-2fc88557bca9)

Edit values.yml and add mysql, rabbitmq elements

![image](https://github.com/tejasp77/DevOps/assets/165159032/29610146-6c98-4ecd-83d3-2871a6c98782)


Run the helm install command and getting error

![image](https://github.com/tejasp77/DevOps/assets/165159032/e0d5996a-b641-49ba-9a38-1cd578c0535c)

Uninstall the release and run again.

![image](https://github.com/tejasp77/DevOps/assets/165159032/f6f6c0e4-9c47-4b0b-80fe-1b61042c0994)

check pods for mysql

![image](https://github.com/tejasp77/DevOps/assets/165159032/167a0c30-1c06-49fd-8f08-b4ba4639ef05)

Getting output as expected.

Add the condition for rabbitmq as well in Chart.yml

![image](https://github.com/tejasp77/DevOps/assets/165159032/2748c6e4-d37f-4e47-8e8a-1e898ca73e6b)

We will get the same output.

**Pass values to dependies at runtime**

Check default values for mysql from values.yml file

![image](https://github.com/tejasp77/DevOps/assets/165159032/fb1b8fe4-f10f-4fd3-b3f5-39673b31c21a)

![image](https://github.com/tejasp77/DevOps/assets/165159032/31c470b8-1c69-498c-b623-08e7d2d6423a)

Edit values.yml file and add parameters for mysql element

![image](https://github.com/tejasp77/DevOps/assets/165159032/824ee670-19c1-467c-83b7-d7aaa6f82c36)

Run the helm install command and check the service

![image](https://github.com/tejasp77/DevOps/assets/165159032/7315fcce-9a1e-47e2-96d9-8a27a41420c3)

Getting output as expected.

**Read Values from child chart**

---


[Template Functions and Pipelines](https://helm.sh/docs/chart_template_guide/functions_and_pipelines/)

[Template functions list](https://helm.sh/docs/chart_template_guide/function_list/)

[if Conditional Statement](https://towardslearning.in/conditional-statement-in-helm-template/)

[Flow Control if conditional statement](https://helm.sh/docs/chart_template_guide/control_structures/)

[Iteration in helm](https://towardslearning.in/iterate-in-helm/)

[helm template cleansheet](https://towardslearning.in/helm-template-cheat-sheet/)

[Variable helm template](https://towardslearning.in/variable-in-helm-template/)

[helm configmap from file](https://towardslearning.in/helm-configmap-from-file/)











