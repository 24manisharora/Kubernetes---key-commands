kubectl top node
watch "kubectl top node" [#to watch status every 2 minutes]
kubectl top pod

kubectl logs <pod name | grep <key word>
kubectl exec <pod name> -- cat /log/data.log    [#to view logs from log file]
kubectl logs <pod name> --all-containers=true

kubectl -n <pod name> exec -it data cat /log/data.log    [#to view the Logs]
