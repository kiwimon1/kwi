# Terraform AWS Infrastructure

AWS VPC와 EC2 인스턴스를 Terraform으로 구성한 프로젝트입니다.

## 인프라 구성

### 네트워크
- **VPC**: 10.0.0.0/16
- **Public Subnet**: 10.0.0.0/24 (ap-northeast-2a)
- **Private Subnet**: 10.0.1.0/24 (ap-northeast-2c)
- **Internet Gateway**: Public 서브넷 인터넷 접근
- **NAT Gateway**: Private 서브넷 아웃바운드 접근

### 보안 그룹
- **Public SG**: SSH(22), HTTP(80), HTTPS(443) 허용
- **Private SG**: VPC 내부 통신만 허용

### EC2 인스턴스
- **Public Server**: Amazon Linux, t3.micro
- **Private Server**: Amazon Linux, t3.micro

## 파일 구조
.
├── main.tf # 메인 인프라 구성
├── variables.tf # 변수 정의
├── outputs.tf # 출력값 정의
├── terraform.tf # Provider 설정
├── modules/
│ └── server/
│ └── server.tf # EC2 모듈
└── README.md


## 사용법

### 1. 초기화
```bash
terraform init
2. 계획 확인
terraform plan
3. 배포
terraform apply
4. 삭제
terraform destroy
변수
변수명	기본값	설명
region	ap-northeast-2	AWS 리전
vpc_cidr	10.0.0.0/16	VPC CIDR 블록
public_subnet_cidr	10.0.0.0/24	Public 서브넷 CIDR
private_subnet_cidr	10.0.1.0/24	Private 서브넷 CIDR
출력값
VPC ID

Subnet IDs

Security Group IDs

Internet Gateway ID

Server IPs

요구사항
Terraform >= 1.0

AWS CLI 설정

AWS 자격 증명 EOF
