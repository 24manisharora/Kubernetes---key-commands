# Kubernetes-key-commands
These are the KEY commands used in Kubernetes and might also be very  useful in CKA/CKAD/CKS exams. Please note that these notes are written keeping Beginners as well in mind for an easier underdstanding.

PODS - commands 1.20 onwards

    kubectl get pods                    [# This command is used to list all the Pods in DEFAULT Namespace]
    
    kubectl get pods -o wide            [# This command is used to list all the Pods in DEFAULT Namespace with added details like IP Addresses]

    kubectl -n APP-DATA get pods        [# This command is used to list all the Pods in APP-DATA Namespace]
    or
    kubectl get pods -n APP-DATA        [# This command is used to list all the Pods in APP-DATA Namespace]

    kubectl run nginx --image=nginx     [# This command is used to CREATE an NGINX Pod with nginx Image]
    
    kubectl run custom-nginx --image=nginx  --port=8080    [# This command is used to Create Pod & expose on Container Port 8080]

  
    kubectl describe pod webapp         [# This command is used to View Details of the Pods named as webapp]
    
    kubectl describe pod <pod name> | grep -i image        [# This command is used to view the IMAGE used on a pod]
    
    
Following commands are used to CREATE a POD using YAML:

    kubectl run redis --image=redis --dry-run=client -o yaml > pod.yaml      [# STEP:1 - This command is used to prepare a dry-run / pod template in YAML]
    vi pod.yaml       [# STEP:2 - This command is to edit or view the YAML file in vi / vim editor. Following is the view of the vim editor where we edit the YAML to add our desired data as per requirement. To edit data inside vi editor press i and to SAVE and EXIT hit ESC :wq & ENTER. To exit Vi/Vim without saving, type :q and hit Enter or simply press SHIFT+ZZ ]
       
    apiVersion: v1
    kind: Pod
    metadata:
      creationTimestamp: null
      labels:
        run: redis
      name: redis
    spec:
      containers:
      - image: redis
        name: redis
      resources: {}
      dnsPolicy: ClusterFirst
      restartPolicy: Always
    status: {}
       


    kubectl create -f  pod.yaml     [# STEP:3 - This command is used to CREATE POD using template in YAML]
    kubectl apply -f  pod.yaml      [# STEP:3 - This command is used to APPLY the changes on an existing POD template in YAML]
       

Follwing command is to EDIT the pod. 

    kubectl edit pod redis    
    
However, we CANNOT edit specifications of an existing POD other than the below.

    spec.containers[*].image
	  spec.initContainers[*].image
	  spec.activeDeadlineSeconds
	  spec.tolerations

If it's really required to EDIT them, any of the following 2 options can be used:
Option 1: Edit / save yaml file on temp:
  
    kubectl edit pod <pod name>                         [Step 1]
    kubectl delete pod <pod name>                       [Step 2]
    kubectl create -f /tmp/kubectl-edit-mk8svb.yaml     [Step 3 - This tmp path will be shown on the terminal once an error message shows after unsuccessful EDIT command. This tmp path will be different in different terminals/machines]

       
       
    
