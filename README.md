
# Kubernetes

 Architecture of Kubernetes

 ![Kubernetes](https://github.com/Subhabrata2468/Kubernetes-/blob/master/Architecture%20of%20Kubernetes.png)

**Kubernetes (K8s) is a container orchestration platform that automates the deployment, scaling, and management of containerized
applications. Its architecture consists of several key components:** 

* ***MASTER NODE***

    - **API Server:** Central control point for Kubernetes; exposes the Kubernetes API, intraction with user takes place.

    - **Controller Manager:** Maintains the desired state, ensuring the cluster meets the defined configurations.

    - **Kube-Scheduler:** Assigns workloads to nodes based on resource availability and constraints,creation and management of pods takes place  
    
    - **etcd:** Consistent and distributed key-value store storing configuration data and state information for the cluster.


* ***WORKER NODE***

    - **Kube Proxy:** Maintains network rules and enables communication between pods and external traffic.

    - **Kubelet:** Agent running on each node, responsible for communication with the master and managing containers on the node.

    - **Container Runtime:** Software responsible for running containers, often Docker or containerd.

    - **Pods:**  The smallest deployable units in Kubernetes, containing one or more containers. Pods run on nodes and are managed by the control plane.
