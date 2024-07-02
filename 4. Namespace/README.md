
# ***Namespace***
 - A way to organize and isolate resources within a cluster..

 - Provides a virtual cluster within a physical cluster

 - Allows multiple teams or applications to coexist within the same Kubernetes cluster

 - Each namespace has its own set of resources, such as pods, services, storage volumes that are isolated from resources in other namespaces.

 - This helps to prevent naming conflicts between resources and allows different teams or applications to manage their own resources independently

 - Namespaces provide a way to organize resources and apply resource quotas, network policies, and other settings at a namespace level

- For example, you can limit the number of pods or services that can be created in a namespace, or restrict network traffic between pods in different namespaces.

Example
1.namespace-with-app-namespace.yml
![deployment](https://github.com/Subhabrata2468/Kubernetes-/blob/master/4.%20Namespace/diagram.png)

#### Commands based on namespace

1. To create a namespace
    ```bash
    kubectl get namespaces
    ```

    or Create the yaml file
    ```bash
    apiVersion: v1 
    kind: Namespace 
    metadata:
     name:dev
    ```

1. List all namespaces:
    ```bash
    kubectl get namespaces
    ```
1. Delete a namespace:
    ```bash
    kubectl delete namespace <namespace_name>
    ```
1. Switch context to a namespace:
    ```bash
    kubectl config set-context --current --namespace=<namespace_name>
    ```
1. View resources in a specific namespace:
    ```bash
    kubectl get pods --namespace=<namespace_name>
    ```
1. Create or apply resources in a specific namespace:
    ```bash
    kubectl apply -f <yaml_file> --namespace=<namespace_name>
    ```
1. Describe a namespace:
    ```bash
    kubectl describe namespace <namespace_name>
    ```
1. To see all the resources present in the namespace:
    ```bash
    kubectl get all -n <namespace_name>
    ```
1. To delete resources present in the namespace:
    ```bash
    kubectl delete pods,services,deployments --all -n <namespace_name>
    ```        
1. Edit a namespace:
    ```bash
    kubectl edit namespace <namespace_name>
    ```
1. Get events related to a namespace:
    ```bash
    kubectl get events --namespace=<namespace_name>
    ```
1. Resource quotas for a namespace:
    ```bash
    kubectl get resourcequota --namespace=<namespace_name>
    ```
1. LimitRange for a namespace:
    ```bash
    kubectl get limitrange --namespace=<namespace_name>
    ```

### ***Resource quotas***

1. A way to limit the amount of compute resources that can be consumed by a set of pods in a namespace.

1. A resource quota is defined as a Kubernetes object that specifies the maximum amount of CPU, memory, and other resources that can be used by pods in a namespace 

1. If a ResourceQuota is applied to a namespace but no resource constraints are defined for the pods in the template section of a Deployment YAML file, then the Deployment and ReplicaSet will still be created. However, no pods will enter the running state, as the ResourceQuota will prevent them from consuming any resources

EXAMPLE 
2.namespace-with-resource-quota.yml

### ***LimitRange***

1. LimitRange is a resource object that is used to specify default and maximum resource limits for a set of pods in a namespace When a LimitRange is applied to a namespace, it will only affect newly created pods.

1. Existing pods will not have their resource limits automatically updated to match the LimitRange settings

1. LimitRange is used to set default and maximum resource limits for individual pods or containers within a namespace, while ResourceQuota is used to set hard limits on the total amount of resources that can be used by all the pods in a namespace

Example :
3.namespace-with-LimitRange.yml

***NOTE:***
LimitRange is used to set default and maximum resource limits for **individual pods or containers within a namespace**, while ResourceQuota is used to set hard limits on the **total amount of resources** that can be used by all the pods in a namespace


![final](https://github.com/Subhabrata2468/Kubernetes-/blob/master/4.%20Namespace/namespace.png)
