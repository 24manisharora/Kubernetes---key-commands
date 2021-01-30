kubectl expose pod redis --port=6379 --name redis-service
kubectl run busybox --image=busybox:1.28 --port=80 --expose
kubectl explain pod --recursive | less
kubectl explain persistentvolume --recursive | less
kubectl explain pod --recursive | grep -A5 tolerations
kubectl -n kube-system get pods | grep proxy
kubectl -n kube-system get pods -o wide| grep proxy
kubectl create cm test-config-map --from-literal=APP_DATA=TEST
kubectl explain pods --recursive | grep envFrom -A3
kubectl delete pod <pod-name> --grace-period=o --force
openssl x509 -in /etc/kubernetes/pki/apiserver.crt -text | grep CN     [to check Kube API Server Certificate configurations]
kubectl config --kubeconfig=/root/my-kube-config use-context <context name>  [To change context in kubeconfig file.]
kubectl create secret docker-registry private-reg-cred --docker-username=dock_user --docker-password=dock_password --docker-server=myprivateregistry.com:5000 --docker-email=dock_user@myprivateregistry.com
