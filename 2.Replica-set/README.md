
# ***Replica-set***
 * It ensures a specified number of replica Pods are running at all times.

 * If a Pod managed by a ReplicaSet fails or is deleted, the ReplicaSet will automatically create a new replica to replace it.

#### Example:
![replicaset](https://github.com/Subhabrata2468/Kubernetes/blob/trash/2.Replica-set/Replicaset.png)

#### _COMMANDS BASED ON REPLICASET_

1. **Create a ReplicaSet from a YAML file:**
    ```bash
    kubectl apply -f your-replicaset.yaml

    ```

1. **List all ReplicaSets:**
    ```bash
    kubectl get rs
    ```

1. **Describe a specific ReplicaSet:**
    ```bash
    kubectl describe rs your-replicaset-name
    ```

1. **Scale a ReplicaSet:**
    ```bash
    kubectl scale rs your-replicaset-name --replicas=3
    ```

1. **Delete a ReplicaSet**
    ```bash
    kubectl delete rs your-replicaset-name
    ```

1. **Edit a ReplicaSet:**
    ```bash
    kubectl edit rs your-replicaset-name
    ```

1. **List pods controlled by a specific ReplicaSet:**
    ```bash
    kubectl get pods -l your-label-selector
    ```

Replace **your-replicaset.yaml** with the path to your ReplicaSet YAML file and **your-replicaset-name** with the name of your ReplicaSet.
