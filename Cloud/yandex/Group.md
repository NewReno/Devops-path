### Create group of instance in spec.yaml
```
name: my-group
service_account_id: ajeu495h1s9tn1rorulb
 
instance_template:
    platform_id: standard-v1
    resources_spec:
        memory: 2g
        cores: 2
    boot_disk_spec:
        mode: READ_WRITE
        disk_spec:
            image_id: fd8fosbegvnhj5haiuoq 
            type_id: network-hdd
            size: 32g
    network_interface_specs:
        - network_id: enpnr4onfs6ihtoao32u
          primary_v4_address_spec: { one_to_one_nat_spec: { ip_version: IPV4 }}
    scheduling_policy:
        preemptible: false
    metadata:
      user-data: |-
        #cloud-config
          package_update: true
          runcmd:
            - [ apt-get, install, -y, nginx ]
            - [/bin/bash, -c, 'source /etc/lsb-release; sed -i "s/Welcome to nginx/It is $(hostname) on $DISTRIB_DESCRIPTION/" /var/www/html/index.nginx-debian.html']
 
deploy_policy:
    max_unavailable: 1
    max_expansion: 0
scale_policy:
    fixed_scale:
        size: 3
allocation_policy:
    zones:
        - zone_id: ru-central1-a
 
load_balancer_spec:
    target_group_spec:
        name: my-target-group
```
### Image ID
```
yc compute image list --folder-id standard-images 
```
### Create group
```
yc compute instance-group create --file specification.yaml  
yc compute instance-group list 
```
### Load balancer
```
yc load-balancer network-load-balancer create --help 
yc load-balancer network-load-balancer create --region-id ru-central1 --name my-load-balancer --listener name=my-listener,external-ip-version=ipv4,port=80
yc load-balancer target-group list
```
### Attache group
```
yc load-balancer network-load-balancer attach-target-group b7r97ah2jn5rmo6k1dsk   --target-group target-group-id=b7r7cmdopr7bejtmj7dt,healthcheck-name=test-health-check,healthcheck-interval=2s,healthcheck-timeout=1s,healthcheck-unhealthythreshold=2,healthcheck-healthythreshold=2,healthcheck-http-port=80
```
### Health check
```
yc load-balancer network-load-balancer target-states b7rkqsnocbl7vgrbv6br --target-group-id b7r675m18nf06i36erd5
```