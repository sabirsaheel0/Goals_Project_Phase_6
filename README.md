# Promethus Screenshot

<img width="1914" height="963" alt="Screenshot 2026-01-29 215920" src="https://github.com/user-attachments/assets/78fb0f3c-1e9d-43cf-8c13-956ce686d6a0" />


# Grafana Dashboards Screenshot
<img width="1910" height="958" alt="Screenshot 2026-01-29 222822" src="https://github.com/user-attachments/assets/84fde4b9-b997-4e2e-a475-5d843b6b6b2f" />

<img width="1917" height="967" alt="Screenshot 2026-01-29 222852" src="https://github.com/user-attachments/assets/4dbc3d3f-07e8-43e2-b3d3-16c5f3e7e6d1" />

<img width="1919" height="1034" alt="Screenshot 2026-01-29 222942" src="https://github.com/user-attachments/assets/53adc775-0013-4f4a-bf16-c317aea4ba89" />


# phase 6 monitor everything
## Environment
this edition is tested on 
- kubeadm server
- installed on on prem vmware instances
- 1 master 2 worker
## installation
- we will use this helm chart, kube-prometheus stack
https://github.com/prometheus-community/helm-charts/tree/main/charts/kube-prometheus-stack
- execute
 ```
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo update
helm install test1 prometheus-community/kube-prometheus-stack \
	--namespace monitor \
	--create-namespace \
	--values values.yaml
```

- install goals app
```
kubectl create ns goals-ns
kubens goals-ns
kubectl apply -f ./k8s
```

## expose
- port forward promethues and grafana dashboard
- prometheus in not password secured , so no need of credentials
- get the grafana creds form the secrets

## visualize
- import the grafana dashboards from the `./grafana-dashboards/`directory


## feature to be introduced
- pvc, pv should be added and monitored
	- total pv, pvc
	- used pv,pvc
	- % used pv,pvc
	- number of pv,pvc
	- dangling pvc,pv
	- ...
	- ...
