
# ***Service***
 - A core component in Kubernetes that are used to manage networking and traffic flow within a cluster.

 - Provide a ***stable IP address*** and ***DNS name*** for a set of pods and allow for communication between different components within and outside of the application.

 - Enable ***load balancing*** , ***service discovery*** and ***traffic management***, making them a critical component for building scalable and resilient applications in Kubernetes.


   #### *IMPORTANT*

   1. *If a pod fails or is removed from the service, ***controller*** will automatically remove it from the list of endpoints for the service. This ensures that traffic is not sent to a non-existent pod.*

   1. *When a pod managed by a ***deployment*** fails, The controller creates a new pod to replace the failed pod.*

   1. *Once the new pod is running and ready,***service's endpoint controller*** will add it back to the list of endpoints for the service, allowing traffic to be routed to it(used labels and selectors to discovery)*

   1. *Ip will varies from the failed pods* 

    #### NOTE

    * services use ***labels*** and ***selectors*** to ***discover and route*** traffic to the pods that are part of the service.

    * Each service has a unique IP address and DNS name that can be used to access the pods that provide the service.


   ### Types of services in K8s

   1. **ClusterIP**: Exposes the service on a *cluster-internal IP only*. This means the service is only reachable within the cluster. This is the ***default type*** of service.

   1. **NodePort**: Exposes the service on *each Node’s IP at a static port*. A service of type NodePort allocates a specific port on every node in the cluster, which can be accessed from outside the cluster using the node's IP address .

   1. **LoadBalancer**: Exposes the service *externally using a cloud provider’s load balancer*. The cloud provider assigns a public IP address to the service, and the external load balancer distributes incoming traffic to the service.

    * When you create a Service of type LoadBalancer, k8s will automatically create a NodePort and ClusterIP for the Service.

   1. **ExternalName**: Maps the service to the contents of the externalName field (e.g., a DNS name). This type of service *allows accessing external services by DNS name without requiring a local mirror of the external service.*
   
   
   ### To expose a service to the outside world in k8s

   * **LoadBalancer Service** : This method requires that your cloud provider supports LoadBalancer services, and it can incur additional costs.

   * **NodePort Service** : This type of service exposes the service on a static port on each node in the cluster, which can be accessed from outside the cluster using the node's IP address.

   * **Ingress** : An Ingress is a Kubernetes resource that defines a set of rules for routing external HTTP(S) traffic to a service.Ingress resources require an Ingress controller to be deployed in the cluster, which is responsible for implementing the routing rules. Ingress controllers are available for many popular web servers, such as Nginx.

![Services](https://github.com/Subhabrata2468/Kubernetes-/blob/master/6.Service%20%26%20Endpoint/Services.png)



#### Commands based on Services

1. Get information about services:
    ```bash
    kubectl get services
    ```
1. Describe a service:
    ```bash
    kubectl describe service <service-name>
    ```
1. Delete a service:
    ```bash
    kubectl delete service <service-name>
    ```
1. Expose a deployment as a service:
    ```bash
    kubectl expose deployment <deployment-name> --port=<port> --target-port=<target-port> [--type=NodePort|LoadBalancer|ClusterIP]
    ```
1. Edit a service:
    ```bash
    kubectl edit service <service-name>
    ```
1. Patch a service:
    ```bash
    kubectl patch service <service-name> --patch='<patch>'
    ```
1. Port forwarding:
    ```bash
    kubectl port-forward <pod-name> <local-port>:<remote-port>
    ```


### ***Endpoint***

 Endpoints are objects that represent a set of network addresses and ports used to access a Kubernetes service. These addresses typically correspond to the pods that are targeted by the service.
 Endpoints allow Kubernetes services to dynamically update the list of back-end pods that they route traffic to. This is especially useful in scenarios where pods are created, scaled, or terminated dynamically, as the service can automatically reflect these changes without manual intervention.

SAMPLE
```bash 
apiVersion: v1
kind: Endpoints
metadata:
  name: my-endpoints
subsets:
  - addresses:
      - ip: 192.168.1.1
      - ip: 192.168.1.2
    ports:
      - port: 80
        name: http
      - port: 443
        name: https

```
