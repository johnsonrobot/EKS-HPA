### 1. Install Metrics Server
> kubectl apply -f https://github.com/kubernetes-sigs/metrics-server/releases/latest/download/components.yaml
#### Verify
> kubectl get deployment metrics-server -n kube-system

### 2. Deploy Application
> kubectl apply -f hpa.yaml

#### Check Resources
> kubectl get all

#### Verify application
> kubectl get nodes -o wide
#### Access browser. You should modify security group
> http://<"WorkerNode IP">:<"NodePort">

### 3. Create HPA resource for deployment
> kubectl autoscale deployment hpa-deploy --cpu-percent=1 --min=1 --max=10

#### Describe HPA
> kubectl describe hpa/hpa-deploy

#### List HPA
> kubectl get horizontalpodautoscaler.autoscaling/hpa-deploy