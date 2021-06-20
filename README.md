# Matsoo Deployment with AWS CloudFormation 

## YAML files processes

Deploying following configuration files in sequence in AWS CloudFormation:

### for CDN 
1. `eks-auth`, `network`, `public-repos`: no dependence between others 
2. `eks-cluster`: need to wait until `network` is ready to get the network configuration
3. `efs`: need to wait util `eks-cluster` creating the security group for the nodes; since EFS also using the same security group

### for Video 360's content serving:

1. `content-storages`

## Other required processes

aws-cli prerequisite

```
$ aws --version
aws-cli/2.2.10 Python/3.8.8 Linux/4.15.0-135-generic exe/x86_64.ubuntu.18 prompt/off
```

### Setup `kubectl` accessing permission

```
$ aws eks update-kubeconfig --region $REGION --name $EKS_CLUSTER_NAME
```

### Get token for ECR public registry

```
$ aws ecr-public get-login-password --region $REGION | docker login --username AWS --password-stdin public.ecr.aws
```
