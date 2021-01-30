 kubectl get ns                                 [# ns is short for NAMESPACE]
 kubectl get ns --no headers | wc -1            [# This command is get the TOTAL COUNT of NAMEPSACES available in Cluster. Add "--no headers" switch/option will ignore the Header row from the total count.]
 kubectl get -n <name of namespace> get pods --no headers 
 
 kubectl -n <name of namespace>  get pod <New Pod Name> -f  pod.yaml  [# This command will list all pods available within a namespace. YAML format]
 
 kubectl get pods --all-namespaces | grep blue    [# This command will list all pods in ALL NAMESPACE]
 
 
