# Developers Guide

```{admonition} Disclaimer  
Please note that this module is currently under development and may contain partially implemented features, therefore it is not supported in the current release.
```

## Debug Intel Data Center GPU Driver Container Image on OpenShift Cluster 

To debug the driver container image, please make sure the OpenShift cluster is provisioned with Intel Data Center GPU Flex cards available on the cluster nodes. 

```{note}   
The following operations are verified on OCP-4.11 and OCP-4.12 cluster with Intel® Data Center GPU Flex 140
```

### Debugging Driver Build 
Firstly, [Red Hat OCP buildconfig](https://docs.openshift.com/container-platform/4.11/cicd/builds/understanding-buildconfigs.html) is used to debug driver building process. The Dockerfile section in [driver-build.yaml](driver-build.yaml) can be updated to debug the building and packaging of the driver container Image. 

Using the below command to deploy the buildconfig and start a building process on openShift cluster. 
```
$ oc apply –f driver-build.yaml
```

If everything runs smoothly, the image created from the building process will be saved into [Red Hat OpenShift image stream](https://docs.openshift.com/container-platform/4.11/openshift_images/image-streams-manage.html), which can be used to debug the deployment of driver container image on the cluster. 

### Debugging Permission
Before that we need to create the proper [service account](https://kubernetes.io/docs/concepts/security/service-accounts/) with the proper permission to deploy and debug the driver container image. Even now the privileged permission is used, the least permission is needed to deploy the driver. 

Using below command to create the service account with [driver-rbac.yaml](driver-rbac.yaml)   
```
$ oc apply –f driver-rbac.yaml
```

### Debugging Driver Deployment 
Now driver [driver-deploy.yaml](driver-deploy.yaml) can be used to deploy and debug the driver container image 
```
  $ oc apply –f driver-deploy.yaml
```

### Debugging Driver
Below command can be used to log into the driver container to do further debugging work 
```
$ oc debug –n <namespace>  pod/<pod_name>
```

Below command can also be used to debug the node where the driver container is running if further debugging on the work node is needed 
```
$ oc debug –n <namespace> node/<node_name> 
```