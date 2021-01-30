kubectl create secret generic db-secret --from-literal=DB_Host=sql01 --from-literal=DB_user=root --from-literal=DB_Password=password123

kubectl describe secrets db-secret
