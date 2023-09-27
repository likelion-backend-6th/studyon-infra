<h1 align=center>Infra for Study On</h1>

[Study On](https://github.com/likelion-backend-6th/studyon) 프로젝트를 배포하기 위한 `Infra` 파일 저장소

- [Terraform](#terraform)
  - [Prerequisite](#prerequisite)
  - [Setup](#setup)
    - [변수 설정](#변수-설정)
    - [Object Storage (s3) key 설정](#object-storage-s3-key-설정)
  - [Usage](#usage)
    - [kubernetes 클러스터 구성](#kubernetes-클러스터-구성)
    - [클러스터 연결](#클러스터-연결)


# Terraform

- kubernetes 클러스터 구성

## Prerequisite

- Terraform > v1.5.7

## Setup

### 변수 설정

`terraform/k8s/terraform.tfvars`

```tf
NCP_ACCESS_KEY = "ncp_access_key"
NCP_SECRET_KEY = "ncp_secret_key"
```

### Object Storage (s3) key 설정

`terraform/k8s/.credentials`

```tf
[default]
aws_access_key_id = "ncp_access_key"
aws_secret_access_key = "ncp_secret_key"
```

## Usage

### kubernetes 클러스터 구성

```bash
cd terraform/k8s
terraform init
terraform plan
terraform apply
```

### 클러스터 연결

- [ncp-iam-authenticator 설치](https://guide.ncloud-docs.com/docs/k8s-iam-auth-ncp-iam-authenticator)
- [IAM 인증 kubeconfig 생성/업데이트](https://guide.ncloud-docs.com/docs/k8s-iam-auth-kubeconfig)

```bash
ncp-iam-authenticator update-kubeconfig --region KR --clusterUuid <cluster-uuid>
```