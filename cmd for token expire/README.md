
# Command for token expire

* ***kubeadm token create***
A command used in Kubernetes to generate a new authentication token for joining nodes to a cluster. When you initialize a Kubernetes cluster using kubeadm init, it generates an initial bootstrap token, which is used by nodes to join the cluster securely. However, this token has a limited lifespan for security reasons. <br>

To generate a new token after the initial bootstrap token expires or when you need to add additional nodes to the cluster, you can use the kubeadm token create command. This command generates a new token with a default TTL (Time To Live) of 24 hours, which can be adjusted if needed.
    
* Example: 
    - give token 
            kubeadm join 10.0.2.6:6443 --token thhnvv.znp9bps3isf425lt \
	```bash
        kubeadm join 10.0.2.6:6443 --token thhnvv.znp9bps3isf425lt --discovery-token-ca-cert-hash sha256:2aaff809bdd9a12678dca7b447e28440e808d506a40a147224eff42e0786d8ec
    ```

    below command is to generate the token 

    ```bash
     kubeadm token create
    ```
    - A token will generate 
    
    ```bash
        kubeadm join 10.0.2.6:6443 --token <new_token> --discovery-token-ca-cert-hash sha256:2aaff809bdd9a12678dca7b447e28440e808d506a40a147224eff42e0786d8ec
    ```
    * Replace **<new_token>** with the newly generated token.

* To customize the duration of token 
    ```bash
        kubeadm token create --ttl <duration>
    ```
    Replace <duration> with the desired time duration for the token's TTL. The duration can be specified in the format **5h**, **30m**, or **1d** for **hours**, **minutes**, and **days** respectively.


