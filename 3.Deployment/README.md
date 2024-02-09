# ***Deployment***
 - A powerful higher-level abstraction that enables you to manage the desired state of your application in Kubernetes.

 - It ensures that a specified number of replicas of your application are always running, by creating and managing other Kubernetes resources like ReplicaSets and Pods.

 - With deployments, you can perform ***rolling updates and rollbacks***, making it easy to update your application without any downtime or quickly revert to a previous version in case of issues.

Example
![deployment](https://github.com/Subhabrata2468/Kubernetes-/blob/master/3.Deployment/Deploment.png)

***IMPORTANT***
```bash
strategy:
    type: RollingUpdate
    rollingUpdate:
      maxUnavailable: 1
      maxSurge: 1       
```
MEANS 
- The strategy type **RollingUpdate** in a Kubernetes deployment ensures smooth updates by gradually replacing old pods with new ones while maintaining availability. It achieves this by:

    - Allowing no more than one pod to be unavailable at any time (**maxUnavailable: 1**), ensuring continuous availability during the update process.
    
    - Permitting Kubernetes to temporarily create one additional pod (**maxSurge: 1**) above the desired number of pods, facilitating a smooth transition by gradually increasing the number of new pods while decreasing the number of old ones.

#### Commands babased on developent

1. Create a Deployment:
    ```bash
    kubectl create deployment <deployment-name> --image=<image-name>
    ```

1. List Deployments:
    ```bash
    kubectl get deployments
    ```

1. Describe Deployment:
    ```bash
    kubectl describe deployment <deployment-name>
    ```

1. Scale Deployment:
    ```bash
    kubectl scale deployment <deployment-name> --replicas=<replica-count>
    ```

1. Update Deployment:
    ```bash
    kubectl set image deployment/<deployment-name> <container-name>=<new-image>
    ```

1. Rollback Deployment:
    ```bash
    kubectl rollout undo deployment/<deployment-name>
    ```

1. Pause and Resume Deployment:
    ```bash
    kubectl rollout pause deployment/<deployment-name>
    kubectl rollout resume deployment/<deployment-name>
    ```

1. View Deployment History:
    ```bash
    kubectl rollout history deployment/<deployment-name>
    ```

1. View Specific Revision Details:
    ```bash
    kubectl rollout history deployment/<deployment-name> --revision=<revision-number>
    ```

1. Rollback to Specific Revision:
    ```bash
    kubectl rollout undo deployment/<deployment-name> --to-revision=<revision-number>
    ```

1. Expose Deployment as a Service:
    ```bash
    kubectl expose deployment <deployment-name> --port=<port> --type=<service-type>
    ```

1. Delete Deployment:
    ```bash
    kubectl delete deployment <deployment-name>

    ```

hese commands should cover most of the basic deployment-related operations in Kubernetes. However, remember to replace **<deployment-name>**, **<image-name>**, **<container-name>**, **<replica-count>**, **<revision-number>**, **<port>**, and **<service-type>** with your actual values.
