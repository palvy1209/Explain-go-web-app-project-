Chalo, ek *real-world example* ke saath Helm ka concept aur usage samajhte hain.  

Maan lo tumhare paas ek application hai jisme 3 environments hain:  
1. *Development (Dev)*  
2. *Quality Assurance (QA)*  
3. *Production (Prod)*  

Har environment ka configuration alag hai, jaise:  
- *Dev*: Small database aur low resources.  
- *Prod*: Large database aur high resources.  

---

### *Step-by-Step Explanation:*

#### 1. *Helm Install karo*  
Pehle Helm ko install kar lo:  
- *Linux/MacOS*:  
  
              curl https://raw.githubusercontent.com/helm/helm/master/scripts/get-helm-3 | bash
  

- *Windows*:  
  Chocolatey se:
  
              choco install kubernetes-helm
  

Install hone ke baad confirm karne ke liye:  

                  helm version


---

#### 2. *Kubernetes Cluster Setup Karo*  
Helm Kubernetes ke saath kaam karta hai. Isliye ek cluster setup hona chahiye. Tumne abhi apne project me *Minikube* use kiya hai, to pehle usko start kar lo:  

              minikube start


             Kubeconfig file ensure karo:  

             kubectl config view


---

#### 3. *Helm Chart Create Karo*  
Apne application ke liye ek Helm chart banao:  

            helm create my-app


Isse ek folder *my-app* banega, jisme yeh structure hoga:  

        my-app/
        ├── charts/
        ├── templates/
        │   ├── deployment.yaml
        │   ├── service.yaml
        │   ├── ingress.yaml
        ├── values.yaml
        └── Chart.yaml


---

#### 4. *Values File Customize Karo*  
Yeh file environment-specific configurations store karti hai.  
*Default values.yaml file*:  

          replicaCount: 1
          image:
            repository: nginx
            tag: latest
            pullPolicy: IfNotPresent
          service:
            type: ClusterIP
            port: 80
          resources:
             limits:
               cpu: 500m
               memory: 512Mi
             requests:
               cpu: 250m
               memory: 256Mi


Ab alag-alag environments ke liye files banao.  

- *values-dev.yaml*:  
  
         replicaCount: 1
         resources:
            limits:
               cpu: 250m
               memory: 256Mi
            requests:
               cpu: 100m
              memory: 128Mi
  

- *values-qa.yaml*:  
  
           replicaCount: 2
           resources:
              limits:
                 cpu: 500m
                 memory: 512Mi
              requests:
                 cpu: 250m
                 memory: 256Mi
  

- *values-prod.yaml*:  
  
           replicaCount: 5
           resources:
              limits:
                 cpu: 1000m
                 memory: 1024Mi
              requests:
                 cpu: 500m
                 memory: 512Mi
  

---

#### 5. *Templates Update Karo*  
templates/deployment.yaml ko customize karo placeholders ke saath:  

          apiVersion: apps/v1
          kind: Deployment
          metadata:
             name: {{ .Release.Name }}
          spec:
             replicas: {{ .Values.replicaCount }}
             template:
               spec:
                 containers:
                 - name: nginx
                   image: "{{ .Values.image.repository }}:{{ .Values.image.tag }}"
                   resources:
                      limits:
                         cpu: {{ .Values.resources.limits.cpu }}
                         memory: {{ .Values.resources.limits.memory }}
                      requests:
                          cpu: {{ .Values.resources.requests.cpu }}
                          memory: {{ .Values.resources.requests.memory }}


---

#### 6. *Deploy Helm Chart*  
Environment-specific values.yaml ke saath chart ko deploy karo:

- *Dev Environment*:  
  
            helm install my-app ./my-app -f values-dev.yaml
  

- *QA Environment*:  
  
            helm install my-app ./my-app -f values-qa.yaml
  

- *Prod Environment*:  
  
            helm install my-app ./my-app -f values-prod.yaml
  

Deployment verify karne ke liye:  

            kubectl get pods
            kubectl get services


---

#### 7. *Update Aur Rollback*  
Deployment ko update karne ke liye:  

              helm upgrade my-app ./my-app -f values-prod.yaml


Agar issue aaye to rollback karne ke liye:  

               helm rollback my-app 1


---

#### *Example Summary*  
Helm tumhare YAML files ko modular aur reusable banata hai, aur tum alag-alag environments ke liye asani se configurations manage kar sakte ho.  
