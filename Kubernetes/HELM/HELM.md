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

[Template Functions and Pipelines](https://helm.sh/docs/chart_template_guide/functions_and_pipelines/)

[Template functions list](https://helm.sh/docs/chart_template_guide/function_list/)

[if Conditional Statement](https://towardslearning.in/conditional-statement-in-helm-template/)

[Flow Control if conditional statement](https://helm.sh/docs/chart_template_guide/control_structures/)

[Iteration in helm](https://towardslearning.in/iterate-in-helm/)

[helm template cleansheet](https://towardslearning.in/helm-template-cheat-sheet/)

[Variable helm template](https://towardslearning.in/variable-in-helm-template/)

[helm configmap from file](https://towardslearning.in/helm-configmap-from-file/)











