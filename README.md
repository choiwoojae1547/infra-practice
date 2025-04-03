# Kubernetes 3-Tier Architecture 실습 프로젝트

### 🏗 프로젝트 개요
Kubernetes 클러스터 환경에서 **3-Tier 아키텍처 (Web - WAS - DB)**를 구성하고, **Flannel CNI** 및 **Prometheus + Grafana 모니터링**을 통합한 인프라 실습 프로젝트입니다. 실제 서비스 운영 환경을 가정하여 실무 중심의 클러스터 설계 및 구현 경험을 목표로 합니다.

---

### 🔧 기술 스택 및 도구

| 구성 요소         | 사용 기술                          |
|-----------------|----------------------------------|
| 가상화 환경        | VMware                           |
| OS              | Ubuntu 24.04 LTS                 |
| Container       | containerd                       |
| Orchestration   | Kubernetes v1.31                 |
| CNI Plugin      | Flannel                          |
| Monitoring      | Prometheus, Grafana              |
| Web Server      | Nginx                            |
| WAS             | Flask (Python)                   |
| DB              | MariaDB                          |
---

### ⚙️ 시스템 구성도

```plaintext
Master Node
 └─ Worker Node 1 (Web): Nginx
 └─ Worker Node 2 (WAS): Flask
 └─ Worker Node 3 (DB): MariaDB
 │
 +─── Monitoring (Prometheus + Grafana)

📁 프로젝트 구성
infra-practice/
├── manifests/
│   ├── namespace.yaml
│   ├── web-deployment.yaml
│   ├── was-deployment.yaml
│   ├── db-deployment.yaml
│   ├── web-service.yaml
│   ├── was-service.yaml
│   ├── db-service.yaml
├── monitoring/
│   ├── kube-prometheus-stack.yaml
├── README.md

🚀 핵심 구현
	•	kubeadm을 이용한 클러스터 설치 및 네트워크 구성
	•	Worker Node마다 역할을 나누고 label 설정
	•	각각의 Node에 Web/WAS/DB pod 배포
	•	서비스 별 ClusterIP / NodePort 설정
	•	Prometheus Stack을 통한 리소스 수집 및 Grafana 대시보드 구축

📊 Grafana 대시보드
	•	노드 리소스 사용량
	•	Pod/컨테이너 상태
	•	Prometheus 쿼리로 실시간 데이터 확인

📌 향후 계획
	•	CI/CD 파이프라인 구성 (GitHub Actions + ArgoCD)
	•	로그 수집기 (EFK 스택) 연동
	•	Spring Boot 기반의 WAS로 전환 실습
	•	Helm Chart로 구성 요소 자동화 배포

🙋‍♂️ 만든 사람
	•	최우재 (Choi Woojae)
	•	Email: choiwoojae1547@gmail.com
	•	Blog: https://fog-mall-84b.notion.site/1cafccb533aa8005a427d7f17bfe5699?pvs=73
