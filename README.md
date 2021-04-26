# sampleapplication
Sample application with custom error page

# build the Docker image
    docker build --no-cache -t custom-default-backend .

# Tag the image so that it is ready to be pushed into DockerHub
    docker tag custom-default-backend:latest amarendra9991/custom-default-backend
    
# Push image to dockerhub
    docker push amarendra9991/custom-default-backend

# Create the k8s resources: 
    kubectl apply -f custom_default_backend.yaml
    helm install nginx-ingress --namespace ingress-nginx stable/nginx-ingress --set defaultBackend.enabled=false,controller.defaultBackendService=ingress-nginx/custom-default-backend
