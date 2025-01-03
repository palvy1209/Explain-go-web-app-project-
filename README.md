Let's break down each component deeply, explaining how it fits into the overall workflow, how to install and use it, and why it's critical for DevOps practices.Let's break down each component deeply, explaining how it fits into the overall workflow, how to install and use it, and why it's critical for DevOps practices.

### *1. Containerization of the Project*

Containerization is a core part of modern DevOps, as it allows developers to package applications along with their dependencies in a portable format, ensuring that they run consistently across different environments.

#### *Step-by-Step Process*:

- *GIT INSTALLATION*:

         sudo apt intall
         sudo apt install git

- *Clone the Repository*:  
  Git is a version control system, and cloning a repository allows you to retrieve the project's source code.
  
                git clone <repository-url>
  
  This command clones the entire GitHub repository to your local machine, where you can inspect and modify the code.

  - * GO LANG INSTALLATION*:

Begin by downloading the latest Go binary release using wget:

                wget https://golang.org/dl/go1.21.2.linux-amd64.tar.gz

Extract the downloaded Go binary release:

                 tar -xf go1.21.2.linux-amd64.tar.gz

Move the Go binary directory to /usr/local/go:

                  sudo mv go /usr/local/go

Add the Go bin directory to your PATH environment variable:

                  sudo echo 'export PATH=$PATH:/usr/local/go/bin' >> ~/.bashrc

Reload your .bashrc file to apply changes:

                  source ~/.bashrc

Verify that Go is installed successfully by running:

                  go version

- *Build the Application*:  
  In Go (Golang), building an application converts the source code into a binary executable file. The binary is a machine-readable file that the operating system can run.
  
              go build -o main
  
  This command compiles the Go code into a main executable. The -o option specifies the output file name.

- *Run the Application*:  
  After building the application, you run it to test if the binary works as expected.

              ./main
  
  Running the binary (main) starts the web application locally, typically accessible via http://localhost:8080 or any port the app binds to.

- *Access the Application*:  
  Once the application is running, open a browser and access it by typing http://localhost:<port>. If everything is set up correctly, the application should load.

### *Docker Installation*:

           sudo yum update -y
    
           sudo yum install -y docker
    
            sudo systemctl start docker
    
              sudo systemctl enable docker
    
               docker --version
    
             sudo usermod -aG docker ec2-user

             sudo systemctl enable docker
             sudo systemctl start docker
             sudo systemctl status docker

    


#### *Creating a Dockerfile*:

A *Dockerfile* is a text file that contains all the instructions needed to build a Docker image, which is a packaged environment for running applications.

- *What is Docker?*  
  Docker is a platform that uses containers to package and distribute applications. A Docker image contains the application and all its dependencies, so it can be run consistently across different environments.

- *Why Multi-Stage Dockerfile?*
  Multi-stage builds help reduce the final image size and improve security. In a multi-stage Dockerfile, the first stage is used to build the application, and the second stage uses a minimal image (distroless) to only include the necessary components (the binary file).

- *Stage 1: Build the Application*:
- 
         dockerfile
         FROM golang:alpine as builder
         WORKDIR /app
         COPY . .
         RUN go build -o main
  
  - FROM golang:alpine as builder: This line sets the base image to golang:alpine, a minimal image with Go pre-installed.
  - WORKDIR /app: Sets the working directory for the subsequent instructions to /app.
  - COPY . .: Copies the current directory (your project) into the /app directory in the container.
  - RUN go build -o main: Builds the application into a binary named main.

- *Stage 2: Create the Final Image*:
- 
  dockerfile
  
        FROM gcr.io/distroless/static
        WORKDIR /
        COPY --from=builder /app/main .
        CMD ["./main"]
  
  - FROM gcr.io/distroless/static: Uses the distroless image, which is a minimal image with no unnecessary libraries, improving security and reducing the size.
  - COPY --from=builder /app/main .: Copies the built binary from the previous stage (builder) into the final image.
  - CMD ["./main"]: Defines the command that will run when the container starts: in this case, running the main binary.

- * Create Docker Image: *
   
        sudo docker build -t <imagename>:<tag>
        docker images
    
  - *UPLOAD DOCKER IMAGE INTO DOCKER HUB*
 
                 docker login -u ramdev284
                 docker push ramdev284/dockerfile:tag
 
---

### *2. Kubernetes Manifest Creation*

Kubernetes is an orchestration platform for managing containerized applications. Manifests (YAML files) are used to describe the state of resources in Kubernetes, including deployments, services, and ingress.

#### *Kubernetes Manifests*:
Kubernetes defines the desired state of an application through YAML files. These files are applied to the cluster using the kubectl apply -f command.

- *Deployment Manifest (deployment.yaml)*:  
  A deployment defines how to run your application in the cluster, including the number of replicas (pods) and the image to use. It ensures the application is always available and scalable.

  Example:

        apiVersion: apps/v1
        kind: Deployment
        metadata:
         name: go-web-app
        spec:
         replicas: 3  # Ensures high availability
         selector:
           matchLabels:
             app: go-web-app
         template:
           metadata:
             labels:
              app: go-web-app
           spec:
             containers:
             - name: go-web-app
               image: go-web-app:latest
               ports:
               - containerPort: 80
  
  - *Replicas*: Ensures that 3 instances of the application (pods) are running at all times.
  - *Selector*: Matches the pods with the specified label (app: go-web-app).
  - *Template*: Defines the pod template, including the container image and port to expose.

- *Service Manifest (service.yaml)*:  
  A service is used to expose your pods to other services or external traffic.
  Example:
  
       apiVersion: v1
       kind: Service
       metadata:
       name: go-web-app
       spec:
         selector:
           app: go-web-app
         ports:
           - protocol: TCP
             port: 80
             targetPort: 80
         type: ClusterIP
   
  - *Selector*: Matches the pods with the specified label (app: go-web-app).
  - *Ports*: Exposes port 80 on the service and maps it to port 80 in the container.
  - *ClusterIP*: Exposes the service only within the Kubernetes cluster.

- *Ingress Manifest (ingress.yaml)*:  
  Ingress resources allow external HTTP/S traffic to reach the services in the cluster.
  Example:
  
          apiVersion: networking.k8s.io/v1
          kind: Ingress
          metadata:
            name: go-web-app-ingress
          spec:
            rules:
            - host: go-web-app.local
              http:
                paths:
                - path: /
                  pathType: Prefix
                  backend:
                    service:
                      name: go-web-app
                      port:
                        number: 80
  
  - *Host*: Defines the domain name for external access.
  - *Paths*: Specifies the URL path that should route traffic to the service.

---

### *3. Setting Up Kubernetes Cluster with Minikube*

Minikube is a local Kubernetes cluster used for development and testing.

#### *Installing Minikube*:
- *Linux*:
  
         curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
         sudo install minikube-linux-amd64 /usr/local/bin/minikube

- *Provide execute permission*:

         sudo chmod +x minikube-linux-amd64

- *start a cluster using the Docker driver:*

                     minikuber start --driver=docker

                      newgrp docker
                      minikube status

  - *SETUP KUBECTL*
    
                    curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
                    ls
                    chmod +x kubectl
                    sudo mv kubectl /usr/local/bin/
                    kubectl version --client
                    kubectl config use-context minikube  # this command set to kubectl to intreact to minikube clusters
                    kubectl config current-context
                    kubectl get nodes

  
- *Windows*:
  You can install Minikube via *Chocolatey* or manually from the Minikube GitHub releases page.

#### *Starting Minikube*:
To start a Minikube cluster, run the following command:

        minikube start

This command initializes a local Kubernetes cluster inside a VM or a container.

#### *Check Cluster Status*:
After starting the cluster, you can check the status of the cluster and nodes:

          kubectl cluster-info


#### *Setting Up Docker Environment to Minikube*:
To build Docker images directly inside Minikube:

        eval $(minikube docker-env)


#### *Building and Deploying in Minikube*:
Once your Docker environment is set to Minikube, build your Docker image:

       docker build -t go-web-app:latest .

Then, apply the Kubernetes manifests:

       kubectl apply -f deployment.yaml
       kubectl apply -f service.yaml
       kubectl apply -f ingress.yaml
       kubectl get deployment
       kubectl get srv
       kubectl get ing


---

### *4. Ingress Controller Configuration in Minikube*

Minikube includes an Ingress controller add-on, which allows external HTTP/S traffic to reach your services inside the cluster.

#### *Enable Ingress in Minikube*:

        minikube addons enable ingress


This command enables the Ingress controller, which allows you to manage external access to services.

#### *Verify Ingress Controller*:
Check that the Ingress controller is running in the kube-system namespace:

         kubectl get pods -n kube-system


#### *Accessing the Application*:
1. *Get Minikube IP*:
   To find the IP address of your Minikube instance:
   
          minikube ip
   

2. *Update /etc/hosts*:
   Add the Minikube IP and the domain defined in the Ingress file (go-web-app.local) to your /etc/hosts:
   
             sudo nano /etc/hosts
             192.168.99.100 go-web-app.local
   

3. *Access Application in Browser*:
   Now, you can access the application through http://go-web-app.local.

---

### *5. Helm Chart Creation*

Helm is a Kubernetes package manager that simplifies deploying applications. Helm packages applications as *charts* and provides an easy way to manage Kubernetes applications.

#### *Installing Helm*:
- *Linux*:
  
            curl https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3 | bash
  

- *Windows*:
  Install Helm via *Chocolatey* or manually from Helm's GitHub releases page.

#### *Creating a Helm Chart*:
1. *Create a New Chart*:
   
             helm create go-web-app
   

2. *Modify the Chart*:
   - Update the values.yaml to include your Docker image and other settings for the application.
   - Modify templates like deployment.yaml, service.yaml, and ingress.yaml to ensure they match your app's configuration.

3. *Install the Chart*:
   Install the chart on your Kubernetes cluster:
   
             helm install go-web-app ./go-web-app

   
          ├── helm/
          │   └── go-web-app-chart/
          │       ├── Chart.yaml
          │       ├── values.yaml
          │       ├── templates/
          │       │   ├── deployment.yaml
          │       │   ├── service.yaml
          │       │   └── ingress.yaml
          │       └── charts/
          ├── Dockerfile
          ├── go.mod
          ├── go.sum
          └── .github/
              └── workflows/
                 └── ci-cd.yml
        
---

### *6. Continuous Integration and Delivery (CI/CD)*

#### *GitHub Actions for CI*:
GitHub Actions automates the process of building and testing code when changes are made in the repository.

1. *Create Workflow File*:
   Create a .github/workflows/ci.yml file:
   
  # CICD using GitHub actions

name: CI/CD

# Exclude the workflow to run on changes to the helm chart
          on:
            push:
              branches:
                - main
              paths-ignore:
                - 'helm/**'
                - 'k8s/**'
                - 'README.md'

           jobs:

            build:
              runs-on: ubuntu-latest

              steps:
              - name: Checkout repository
                uses: actions/checkout@v4

              - name: Set up Go 1.22
                uses: actions/setup-go@v2
                with:
                  go-version: 1.22

              - name: Build
                run: go build -o go-web-app

              - name: Test
                run: go test ./...
  
            code-quality:
              runs-on: ubuntu-latest

              steps:
              - name: Checkout repository
                uses: actions/checkout@v4

              - name: Set up Go
                uses: actions/setup-go@v2
                with:
                  go-version: 1.22

              - name: Debug Go environment
                run: go env

              - name: Run golangci-lint
                uses: golangci/golangci-lint-action@v6
                with:
                  version: v1.56.2
  
            push:
              runs-on: ubuntu-latest

              needs: build

              steps:
              - name: Checkout repository
                uses: actions/checkout@v4

              - name: Set up Docker Buildx
                uses: docker/setup-buildx-action@v1

              - name: Login to DockerHub
                uses: docker/login-action@v3
                with:
                  username: ${{ secrets.DOCKERHUB_USERNAME }}
                  password: ${{ secrets.DOCKERHUB_TOKEN }}

              - name: Build and Push action
                uses: docker/build-push-action@v6
                with:
                  context: .
                  file: ./Dockerfile
                  push: true
                  tags: ${{ secrets.DOCKERHUB_USERNAME }}/go-web-app:${{github.run_id}}

            update-newtag-in-helm-chart:
              runs-on: ubuntu-latest

              needs: push

              steps:
              - name: Checkout repository
                uses: actions/checkout@v4
                with:
                  token: ${{ secrets.TOKEN }}

              - name: Update tag in Helm chart
                run: |
                  sed -i 's/tag: .*/tag: "${{github.run_id}}"/' helm/go-web-app-chart/values.yaml

              - name: Commit and push changes
                run: |
                  git config --global user.email "abhishek@gmail.com"
                  git config --global user.name "Abhishek Veeramalla"
                  git add helm/go-web-app-chart/values.yaml
                  git commit -m "Update tag in Helm chart"
                  git push


   

2. *Run Tests and Build Docker Image*:
   This workflow will run every time you push code to the main branch. It builds the application, runs tests, and pushes the Docker image to a repository.

#### *Argo CD for CD*:
Argo CD is a GitOps continuous delivery tool for Kubernetes that automates the deployment process.

1. *Install Argo CD*:
   Install Argo CD in your Kubernetes cluster:
   
                helm install argo-cd argo/argo-cd --namespace argocd
   

2. *Set Up GitOps*:
   Argo CD can watch your Git repository for changes to the Helm charts and automatically apply those changes to your Kubernetes cluster.

---

### *7. Workflow Summary*

mermaid
graph TD

           A[Clone Repository] --> B[Build Go Application]
           B --> C[Run Application Locally]
           C --> D[Create Dockerfile]
           D --> E[Build Docker Image in Minikube]
           E --> F[Create Kubernetes Manifests]
           F --> G[Deploy Application on Minikube]
           G --> H[Set Up Ingress Controller]
           H --> I[Create Helm Chart]
           I --> J[Setup CI/CD with GitHub Actions and Argo CD]
           J --> K[Automated Deployment and Testing]
           K --> L[Access Application via Browser]


---

### *Conclusion*

This process integrates containerization, Kubernetes orchestration, Helm chart management, and CI/CD automation into a smooth DevOps workflow. By using *Minikube* for local Kubernetes management, *Docker* for containerization, *Helm* for application deployment, and *GitHub Actions/ **Argo CD* for CI/CD, this approach ensures that code is continuously built, tested, and deployed with minimal human intervention.

