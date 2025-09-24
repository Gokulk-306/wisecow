# Summary of Wisecow Kubernetes Deployment

## 1. Docker Image

* Created a Dockerfile for Wisecow app.
* Built and pushed image to GitHub Container Registry.

## 2. Kubernetes Deployment

* Created Deployment `wisecow-deployment` with 2 replicas.
* Pod containerPort set to 4499.

## 3. Kubernetes Service

* Created NodePort Service `wisecow-service`.
* Exposes port 4499 on NodePort 30080.
* Verified endpoints are running.

## 4. Kubernetes Ingress

* Created Ingress `wisecow-ingress-local` with `nginx` ingress class.
* Configured host `wisecow.local`.
* Tested Ingress, confirmed class is correctly picked.

## 5. Local Host Configuration

* Added `192.168.49.2 wisecow.local` to `/etc/hosts`.

## 6. Testing & Access

* Verified app works via:

  * NodePort: `http://192.168.49.2:30080/`
  * Port-forward: `kubectl port-forward svc/wisecow-service 8080:4499`
  * Ingress (if Minikube tunnel works): `http://wisecow.local/`
* Minikube tunnel used but port-forward used as fallback due to tunnel delays.

## 7. GitHub Actions

* Workflow setup to build and push Docker image automatically on repo changes.

## 8. Works that are done

* Used Deployment, Service, Ingress in Kubernetes.
* Resolved IngressClass issue (`class <none>` → `nginx`).
* Verified all endpoints, pods, and services.
* Port-forward confirmed application functionality.
* Demonstrated CI/CD with GitHub Actions.
* Fallback strategy when Minikube tunnel failed.
