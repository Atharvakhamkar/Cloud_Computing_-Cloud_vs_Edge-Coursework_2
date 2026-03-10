# Kubernetes VNF Performance Evaluation

## Overview
Performance evaluation of CoreDNS as a Virtual Network Function (VNF)
deployed on Kubernetes in cloud (kind) and edge (K3s) environments.

## Environments
| Environment | VM | Kubernetes | Version |
|---|---|---|---|
| Cloud | demo-server-1 | kind | v1.35.0 |
| Edge | jenkins-node-1 | K3s | v1.34.5 |

## VNF Selected
CoreDNS v1.11.1 — DNS resolution and service discovery function
relevant to 5G core architecture (3GPP TS 23.501)

## Repository Structure
```
k8s-vnf-project/
├── manifests/
│   ├── coredns-configmap.yaml
│   ├── coredns-deployment.yaml
│   └── coredns-service.yaml
├── results/
│   ├── cloud/
│   │   ├── cloud_test_light.txt
│   │   ├── cloud_test_medium.txt
│   │   └── cloud_test_heavy.txt
│   └── edge/
│       ├── edge_test_light.txt
│       ├── edge_test_medium.txt
│       └── edge_test_heavy.txt
├── queryfile.txt
└── README.md
```

## Quick Deploy
```bash
kubectl create namespace coredns-vnf
kubectl apply -f manifests/coredns-configmap.yaml
kubectl apply -f manifests/coredns-deployment.yaml
kubectl apply -f manifests/coredns-service.yaml
kubectl get all -n coredns-vnf
```

## Performance Results Summary
| Test | Cloud Avg Latency | Edge Avg Latency |
|---|---|---|
| Light 100 QPS | 0.205ms | 0.309ms |
| Medium 500 QPS | 0.176ms | 0.227ms |
| Heavy 1000 QPS | 0.342ms | 0.216ms |
