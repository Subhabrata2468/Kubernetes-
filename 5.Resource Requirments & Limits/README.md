
# ***Resource Requirements & limits***
 - Resource requirements and limits are used to specify the amount of CPU and memory resources that a container requires in order to run properly.

 - **Resource requirements** are set in the pod specification and indicate the minimum amount of CPU and memory resources that a container needs to run. Kubernetes uses these requirements to determine which nodes in the cluster have the necessary resources to schedule the pod.

 - **Resource limits** specify the maximum amount of CPU and memory resources that a container is allowed to use. Kubernetes enforces these limits by throttling the container's resource usage if it exceeds the specified limit

 - You can only limit cpu,memory,storage .

 - Default value of 
    * request value 0.5 CPU and memory 256Mi
    * limit value 1 CPU and memory 256Mi

 - When a container reaches or exceeds its memory limit, the Linux kernel's Out of Memory Killer (OOM Killer) is invoked. The OOM Killer is responsible for selecting and terminating processes to free up memory when system memory becomes critically low. By default, Kubernetes lets the OOM Killer select and terminate the process within the container that triggered the OOM condition.

 ![input](https://github.com/Subhabrata2468/Kubernetes-/blob/master/5.Resource%20Requirments%20%26%20Limits/request%20and%20limit%20diagram.png)

#### Commands based on Resource Requirements & limits

1. Viewing Resource Quotas:
    ```bash
    kubectl get resourcequota
    ```

1. Editing Resource Requirements and Limits:
    ```bash
    kubectl edit pod <pod_name>
    ```    

1. Checking Resource Requirements and Limits Validation:
    ```bash
    kubectl apply --dry-run=client -f <pod_yaml_file>
    ```
![output](https://github.com/Subhabrata2468/Kubernetes-/blob/master/5.Resource%20Requirments%20%26%20Limits/request%20and%20limit%20output.png)
