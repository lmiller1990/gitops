 1. Cluster prep
 - Enable the minikube ingress addon (this deploys the nginx Ingress Controller)
 - Make sure Caddy on the host can reach the minikube cluster (minikube IP, NodePort for the ingress)

 2. ArgoCD install
 - Deploy ArgoCD into the cluster (there's a manifest for this)
 - Access the ArgoCD UI (port-forward or NodePort)
 - Connect it to your GitHub repo

 3. The infra repo
 - Create a new repo (e.g., lachlan/infra or homelab)
 - Commit a Deployment manifest for the blog
 - Commit a Service manifest
 - Commit an Ingress manifest (with the blog domain)

 4. ArgoCD app
 - In ArgoCD, create an Application pointing to that repo + path
 - Watch it deploy the blog

 5. Caddy wiring
 - Add a route in Caddy that proxies to minikube-ip:<ingress-nodeport>
 - Your existing DNS record + Caddy TLS handles the rest

 6. Iterate
 - Change the image tag in Git → watch ArgoCD roll it out
 - Break a pod → watch it self-heal
