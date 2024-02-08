
# ***PODS***

* The smallest deployable units of computing that you can create and manage in Kubernetes.

* A Pod is a group of one or more containers, with shared storage and network resources, and a specification for how to run the containers

* Pods encapsulate and manage application processes and are created using a pod specification, which describes the desired state of the pod, including the containers to run, the network configuration, and any storage volumes to use. 

* Pods are scheduled to run on nodes in the cluster by the Kubernetes scheduler and can be managed using labels and selectors to group and organize them based on their attributes

* To run a container, it must be part of a pod. This means that containers cannot be directly brought up in the cluster without being part of a pod


## How creation of container inside the kubernetes takes place
![pod](https://github.com/Subhabrata2468/Kubernetes-/blob/master/1.POD/Kubernetes%20workload%20objects.png)

## Kubernetes workload object
 ![workload](https://github.com/Subhabrata2468/Kubernetes-/blob/master/1.POD/Pod%20creation.png)


* 1.container_with_one_pod.yml
* 2.Mulitple_containers_with_one_pod.yml             
* 3.env_vars_in_pod.yml  
* 4.pod_with_ports.yml   




