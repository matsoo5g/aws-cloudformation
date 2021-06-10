# Matsoo Deployment with AWS CloudFormation 

## YAML files processes

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
