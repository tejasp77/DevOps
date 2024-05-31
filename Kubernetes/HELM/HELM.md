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



