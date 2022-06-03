### Update yc
```
yc components update
```
### Create network
```
yc vpc network create --name my-network 
```
### Create subnetworks
```
yc vpc subnet create --name my-subnet-1 \
  --zone ru-central1-a \
  --range 192.168.1.0/24 \
  --network-name my-network 
```
### Create instance
```
yc compute instance create --name my-instance-3 \
  --hostname my-instance-3 \
  --zone ru-central1-a \
  --create-boot-disk image-family=ubuntu-2004-lts,size=30,type=network-nvme \
  --image-folder-id standard-images \
  --memory 4 --cores 2 --core-fraction 100 \
  --network-interface subnet-name=my-subnet-3,nat-ip-version=ipv4 \
  --async 
```
### Operation info
```
yc operation get ID
```
### Instance list
```
yc compute instance list --format json 
```
### Del instance
```
yc compute instance delete my-instance-2 --async
```
### Create group of instance in spec.yaml
```
name: my-group
service_account_id: ajeu495h1s9tn1rorulb 
instance_template:
    platform_id: standard-v1
    resources_spec:
        memory: 2g
        cores: 2 