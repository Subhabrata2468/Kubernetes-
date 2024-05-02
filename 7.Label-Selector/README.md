
# ***Label & Selector***

#### Label
* Labels are a powerful mechanism for grouping and organizing related objects, such as Pods, Services, Deployments, and more.

*  Labels are key-value pairs that can be attached to Kubernetes objects, and they can be used for a variety of purposes, such as   

    * **grouping related objects** for easy management, 
    * **selecting objects for operations** such as **scaling or updating**
    * enabling fine-grained access control

    * Example :
        ```
        metadata:
            ...
            labels:
                colour: red
                emv: data
        ```

#### Selector
* Example :
     ```
     metadata:
        ...
        selector:
            colour: red
            emv: data
     ```
*  Selectors are used to filter and select objects based on their labels.

* They enable you to group and manage resources that share common characteristics. 

*  Selectors are commonly used in services, deployments, and other objects to define which set of resources they should apply to.

* Cannot have any selector without Label.

* There are two types of selector

    - Equality-based (=,==,!=)
     - Set-based (in,notin,exits)
        - matchLabels
            ```
            matchLabels:
                env: enviroment
            ```
        - matchExpressions
            ```
            matchExpressions:
                - {key: <v> , operator:<v> values: [v1,v2]}
                - {key: <v> , operator:<v> values: [v1,v2]}
            ```
            operators like: In,NotIn,Exit,DoesNotExit

#### Commands based on label and Selectors:
* Listing Pods with Labels :
    ```bash
        kubectl get pods --show-labels

    ```

* Selecting Pods with a Label :
     ```bash
        kubectl get pods -l <key>=<value>
    ```

* Adding a label to an exiting pod
     ```bash
        kubectl label pods <pod-name> <key>=<value>
    ```
* Adding a multiple label to an exiting pod
     ```bash
        kubectl label pods <pod-name> <key>=<value>,<key>=<value>
    ```

***NOTE- it is connection to some parts of services ***
#### Examples:
first link 
![Lebels and selector]()-----------------------------------------------------------------------------------------------------------------
1.  ```
    selector:
        matchExpressions:
                - {key: env , operator:In values: [qa,dev]}
                - {key: appl , operator:In values: [backend]}
    ```
    The pods are - 1,3,6 (_because those pods will apply whose labelabels are {env either for qa or dev} and {appl for backend} only_)
    * here ***In*** means appl has backend value
1. ``` 
    selector:
        matchLabels:
            tech: react
        matchExpressions:
                - {key: env , operator:NotIn values: [prod]}
    ```
    The pods are - none
    * here ***NotIn*** means env should not have pord as a value
### Resources that support set-based requirements
Newer resources, such as **Job, Deployment, ReplicaSet, and DaemonSet** support set-based requirements as well

### In this example there are  pods and services i.e. 3 pods are based on Label and 1 service for selector
* All the 3 pods i.e. pod1,pod2,pod3 must be running to apply the selector 

| POD1     | POD2     | POD3     | service   |
|----------|----------|----------|---------- |
|labels:   | labels:  | labels:  | selector: |
| app: myapp1   | app: myapp2   | app: myapp3  | app: myapp3   |
|  environment: production1   |  environment: production2   |  environment: production3  | environment: production3   |

It means that that labels that attached to the selector ,service of port and targetport will attahed to the POD3


