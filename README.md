# Prerequisites 
1. Install dcos enterprise cli if not installed:
```
dcos package install dcos-enterprise-cli
```

# Create Service Account(s)
Create one service account for all monitoring services, or one account for each service.  
1. Create key pair
```
dcos security org service-accounts keypair monitoring.pem monitoring_pub.pem
```
2. Create service account
```
dcos security org service-accounts create -p monitoring_pub.pem -d "monitoring service account" monitoring
```
The final argument ("monitoring") is the service account id (its name in the UI)
3. Create secret
```
dcos security secrets create-sa-secret --strict monitoring.pem monitoring monitoring_private_key
```

