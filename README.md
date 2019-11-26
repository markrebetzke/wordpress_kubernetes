# wordpress_kubernetes
Example Deployments:
Wordpress Persistent:
https://github.com/markrebetzke/wordpress_kubernetes
Deploy a wordpress instance into the newly created kubernets cluster and keep persistent data with glusterFS.

1. Clone repo
2. Make changes to kustomization.yaml for passwor. //TODO: make this secure
3. Run:
        kubectl apply -k ./
4. Ensure the pods are running by:
        kubectl get pods -n kube-app -o wide
5. Open access to the wordpress frontend
        kubectl port-foward -n wordpress-app <pod_name> 8080:80 &
6. Access via
        curl 127.0.0.1:8080
        SSH local-foward
        SIG VirtualServer rule
        
        
//TODO: Secret storage needs to secured rather than plaintext in the kustomization.yaml
//TODO: Redesign or implement persistent storage. Having databases accessed on shared storage doesn't seem like this would be fit for production. Unsure of what to do in this case

//TODO: Add service to access Wordpress frontend outside of a kubectl port-forward
