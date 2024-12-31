    1  minikube start --driver=docker --memory=2000 --cpus=2
    2  minikube status
    3  kubectl get nodes
    4  kubectl config use-context minikube
    5  sudo kubectl config use-context minikube
    6  minikube kubectl --get nodes
    7  kubectl get nodes
    8  kubectl config current-context
    9  kubectl get nodes
    10  minikube status
    11  kubectl version --client
    12  curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
    13  ls
    14  chmod +x kubectl
    15  sudo mv kubectl /usr/local/bin/
    16  kubectl config use-context minikube
    17  kubectl config current-context
    18  minikube update-context
    19  kubectl get nodes
    20  history
    21  ls
    22  sudo yum install git -y
    23  ls
    24  git init
    25  git clone https://github.com/palvy1209/go-web-app-MAIN.git
    26  ls
    27  cd go-web-app-MAIN
    28  LS
    29  ls
    30  go build -o main
    31  Sudo yum install golang -y
    32  yum install golang -y
    33  sudo yum update -y
    34  yum install golang -y
    35  sudo yum install golang -y
    36  go --version
    37  go version
    38  ls
    39  go run -o main
    40  vi dockerfile
    41  cat dockerfile
    42  ls
    43  mdkir manifest/go-web-app
    44  sudo mdkir manifest/go-web-app
    45  sudo mkdir manifest/go-web-app
    46  sudo mdkir ./manifest/go-web-app
    47  mkdir k8
    48  ls 
    49  cd k8
    50  vi deployment.yaml
    51  vi services.yaml
    52  vi ingress.yaml
    53  ls
    54  cd ..
    55  ls
    56  dockerhub login
    57  sudo dockerhub login
    58  sudo docker login
    59  docker push dockerfile
    60  ls
    61  docker push dockerfile/new
    62  docker build -t dockerfile:1.0
    63  sudo docker build -t dockerfile:1.0
    64  sudo docker build -t dockerfile:tag .
    65  docker images
    66  docker push dockerfile:tag
    67  docker tag 4c897b23b0fa ramdev284:tag
    68  docker push ramdev284:tag
    69  docker images
    70  docker tag 4c897b23b0fa ramdev284/dockerfile:tag
    71  docker images
    72  docker push ramdev284/dockerfile
    73  docker push ramdev284/dockerfile:tag
    74  rm ~/ .docker/config.json
    75  sudo rm ~/ .docker/config.json
    76  sudo -f rm ~/ .docker/config.json
    77  sudo rm ~/ .docker/config.json
    78  docker images
    79  docker rmi ramdev284:tag
    80  docker rmi dockerfile:tag
    81  ls
    82  sudo docker images
    83  docker login
    84  docker login -u ramdev284
    85  docker push ramdev284/dockerfile:tag
    86  history
    87  ls
    88  cd k8
    89  ls
    90  kubectl create deployment deployment.yaml
    91  kubectl create deployment.yaml
    92  kubectl -f deployment.yaml
    93  kubectl apply -f deployment.yaml
    94  kubectl get deployments
    95  kubectl get pods
    96  kubectl apply -f service.yaml
    97  ls
    98  kubectl apply -f services.yaml
    99  kubectl delete deployment deployment.yaml
   100  kubectl delete deployment go-web-app
   101  kubectl get deploymets
   102  kubectl get deployments
  103  ls
  104  vi deployment.yaml
  105  kubectl apply -f deployment.yaml
  106  kubectl get deployment
  107  kubectl apply -f services.yaml
  108  cat serevices.yaml
  109  cat services.yaml
  110  vi services.yaml
  111  kubectl apply -f services.yaml
  112  vi services.yaml
  113  kubectl apply -y services.yaml
  114  kubectl apply -f services.yaml
  115  kubectl get services
  116  kubectl apply -f ingess.yaml
  117  ls
  118  kubectl apply -f ingress.yaml
  119  kubectl get services
  120  kubectl apply -f ingress.yaml
  121  kubectl get services
  122  vi ingress.yaml
  123  kubectl apply -f ingress.yaml
  124  vi ingress.yaml
  125  kubectl apply -f ingress.yaml
  126  vi ingress.yaml
  127  kubectl apply -f ingress.yaml
  128  pip install yamllint
  129  sudo pip install yamllint
  130  eksctl create cluster --name gowebapp-cluster --region us-east-1 
  131  curl --silent --location "https://github.com/weaveworks/eksctl/releases/download/v0.137.0/eksctl_Linux_amd64.tar.gz" -o /tmp/eksctl.tar.gz
  132  tar -xvzf /tmp/eksctl.tar.gz -C /usr/local/bin
  133  sudo tar -xvzf /tmp/eksctl.tar.gz -C /usr/local/bin
  134  ekctl version
  135  eksctl version
  136  eksctl create cluster --name gowebapp-cluster --region us-east-1 
  137  history
  138  eksctl create cluster --name gowebapp-cluster --region us-east-1 
  139  eksctl delete cluster --region=us-east-1 --name=gowebapp-cluster
  140  eksctl create cluster --name gowebapp-cluster --region us-east-1 
  141  eksctl create cluster --name gowebapp-cluster --region us-east-1 --verbose 4
  142  eksctl create cluster --name gowebapp-cluster --region us-east-1 
  143  eksctl delete cluster --region=us-east-1 --name=gowebapp-cluster
  144  sudo eksctl delete cluster --region=us-east-1 --name=gowebapp-cluster
  145  eksctl delete cluster --region=us-east-1 --name=gowebapp-cluster
  146  eksctl create cluster --name gowebapp-cluster --region us-east-1 
  147  eksctl delete cluster --region=us-east-1 --name=gowebapp-cluster
  148  eksctl create cluster --name gowebapp-cluster --region us-east-1 
  149  sudo docker yum install -y
  150  sudo yum update
  151  sudo yum upgrade
  152  sudo yum install docker -y
  153  sudo systemctl enable docker
  154  sudo systemctl start docker
  155  sudo systemctl status 
  156  sudo usermod -aG docker ec2-user
  157  sudo docker --version
  158  docker run hello-world
  159  sudo docker run hello-world
  160  systemctl status docker
  161  sudo docker run hello-world
  162  sudo docker pull hello-world
  163  sudo docker run hello-world
  164  minikube start
  165  curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
  166  sudo install minikube-linux-amd64 /usr/local/bin/minikube && rm minikube-linux-amd64
  167  minikube start
  168  chmod +x minikube-linux-amd64
  169  ls
  170  sudo install minikube-linux-amd64 /usr/local/bin/minikube && rm minikube-linux-amd64
  171  curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
  172  sudo install minikube-linux-amd64 /usr/local/bin/minikube && rm minikube-linux-amd64
  173  ls
  174  ls -a
  175  ls
  176  minikube --version
  177  ls
  178  sudo install minikube-linux-amd64 /usr/local/bin/minikube && rm minikube-linux-amd64
  179  curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
  180  ls
  181  minikube --version
  182  sudo chmod +x minikube-linux-amd64 
  183   minikube version
  184  minikuber start --driver=docker
  185    sudo minikube start --driver=docker
  186   newgrp docker
  187  ls
  188  kubectl get pods
  189  kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v1.11.1/deploy/static/provider/aws/deploy.yaml
  190  kubectl apply -f ingress.yaml
  191  ls
  192  cd go-web-app-MAIN
  193  ls
  194  cd k8
  195  ls
  196  kubectl apply -f ingress.yaml
  197  cat ingress.yaml
  198  sudo yum install yamlfmt
  199  vi ingress.yaml
  200  kubectl apply -f ingress.yaml
  201  cat ingress.yaml
  202  vi ingress.yaml
  203  kubectl apply -f ingress.yaml
  204  kubectl get service
  205  kubectl get nodes -o wide
  206  kubectl get ing
  207  kubectl get svc 
  208  kubectl edit svc go-web-aap
  209  kubectl get svc
  210  kubectl delete svc
  211  kubectl delete svc go-web-aap
  212  kubectl get svc
  213  cat service.yaml
  214  cat services.yaml
  215  vi services.yaml
  216  kubectl apply -f services.yaml
  217  kubectl get svc
  218  kubectl edit svc
  219  kubectl get svc -o wide
  220  kubectl get svc
  221  kubectl edit svc
  222  kubectl get svc
  223  kubectl edit svc
  224  kubectl edit svc go-web-app
  225  kubectl get node -o wide
  226  kubectl get nodes -o wide
  227  cat services.yaml
  228  kubectl delect service go-web-app
  229  kubectl delete service go-web-app
  230  kubectl get svc
  231  vi services.yaml
  232  kubectl apply -f servies.yaml
  233  ls
  234  kubectl apply =f services.yaml
  235  kubectl apply -f services.yaml
  236  kubectl get svc
  237  kubectl edit svc
  238  kubectl edit svc go-web-app
  239  kubectl delete svc go-web-app
  240  vi services.yaml
  241  kubectl apply -f services.yaml
  242  kubectl get svc
  243  cat services.yaml
  244  vi services.yaml
  245  kubectl apply -y services.yanl
  246  kubectl apply -f services.yaml
  247  kubectl get svc go-web-app
  248  kubectl get svc
  249  kubectl edit svc
  250  kubectl get nodes -o wide
  251  ls
  252  cd go-web-app-MAIN
  253  ls
  254  cd k8
  255  ls
  256  kubectl get pods
  257  kubectl get service
  258  kubectl get ingress
  259  Kubectl get nodes -o wide
  260  ls
  261  cd go-web-app-MAIN
  262  ls
  263  cd k8
  264  ls
  265  kubectl get nodes -o wide
  266  aws eks list-clusters
  267  eksctl create cluster gowebapp --region eu-north-1
  268  kubectl get nodes -o wide
  269  kubectl get service
  270  curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
  271  unzip awscliv2.zip
  272  sudo ./aws/install
  273  eksctl create cluster gowebapp --region eu-north-1
  274  eksctl delete cluster gowebapp --region eu-north-1
  275  eksctl create cluster gowebapp --region eu-north-1
  276  eksctl delete cluster gowebapp --region eu-north-1
  277  kubectl version --short
  278  sudo kubectl version --short
  279  which kubectl
  280  kubectl get nodes
  281  kubectl config get-contexts
  282  kubectl cofig use-context
  283  kubectl config use-context
  284  kubectl config use-context minikube
  285  aws eks update-kubeconfig --region eu-north-1 --name gowebapp
  286  kubectl get nodes
  287  sudo kubectl version --short
  288  kubectl version --short
  289  kubectl version --shorts
  290  kubectl version
  291  aws eks describe-cluster --name gowebapp --query "cluster.version" --output text
  292  kubectl version
  293  eksctl get cluster
  294  aws eks describe-cluster --query "cluster.version" --output text
  295  aws eks describe-cluster --name gowebaapp --query "cluster.version" --output text
  296  kubectl version
  297  curl -LO "https://dl.k8s.io/release/v1.25.0/bin/linux/amd64/kubectl"
  298  chmod +x kubectl
  299  sudo mv kubectl /usr/local/bin/
  300  eksctl create cluster gowebapp --region eu-north-1
  301  eks cluster
  302  ls
  303  cd go-web-aap-MAIN
  304  cd go-web-app-MAIN
  305  ls
  306  cd k8
  307  ls
  308  eks cluster
  309  kubectl get pods
  310  kubectl get services
  311  kubectl get svc
  312  kubectl get pod
  313  sudo kubectl get pods
  314  sudo kubectl get ingress
  315  kubectl get nodes
  316  ekctl delete --name gowebapp --region eu-north-1
  317  eks delete --name gowebapp --region eu-north-1
  318  aws eks delete --name gowebapp --region eu-north-1
  319  ekctl delete cluster --name gowebapp --region eu-north-1
  320  sudo ekctl delete cluster --name gowebapp --region eu-north-1
  321  ls
  322  ls
  323  cd go-web-app-MAIN
  324  ls
  325  cd k8
  326  ls
  327  kubectl get pods
  328  kubectl get services
  329  ls
  330  cd go-web-app-MAIN
  331  ls
  332  cd k8
  333  ls
  334  cat ingress
  335  cat ingress.yaml
  336  kubectl get nodes
  337  kubectl version
  338  minikube version
  339  minikube status
  340  kubectl config use-context minikube
  341  kubectl get node
  342  kubectl get service
  343  kubectl get ingress
  344  minikube tunnel
  345  ls 
  346  cd go-web-app-MAIN
  347  ls
  348  cd k8
  349  ls
  350  kubectl get pod
  351  minikube service go-web-app
  352  minikube tunnel
  353  kubectl get serivce
  354  kubectl get serivces
  355  kubectl get ingress
  356  kubectl get service
  357  minikube tunnel
  358  exit
  359  ls
  360  cd go-web-app
  361  ls
  362  cd go-web-app-MAIN
  363  ls
  364  cd k8
  365  ls
  366  cd aws
  367  ls
  368  cd ..
  369  ls
  370  cat deployment
  371  cat deployment.yaml
  372  cat services.yaml
  373  cat ingress.yaml
  374  systemctl docker status
  375  sudo system status docker
  376   sudo systemctl status docker
  377  kubectl get ingress
  378  kubectl get nodes
  379  minikube status
  380  minikube start --driver=docker --memory=1901MB --cpus=2
  381  minikube status
  382  kubectl get nodes
  383  kubectl get service
  384  kubectl get ing
  385  kubectl get deployment
  386  kubectl delete deployment go-web-app
  387  vi deployment.yaml
  388  kubectl apply -f deployment.yaml
  389  kubectl get deployment
  390  kubectl get svc
  391  ping 10.107.65.80:32018
  392  ping http:/go-web-app:32018
  393  sudo vi /etc/hosts
  394  kubectl get ing
  395  kubectl get pods -n ingress-nginx
  396  kubectl get svc -n ingress-nginx
  397  minikube tunnel
  398  tmux new -s minikube-tunnel
  399  sudo yum install tmux -y
  400  tmux -V
  401  tmux new -s minikube-tunnel
  402  sudo yum uninstall tmux -y
  403  sudo yum uninstall nohup -y
  404  nohup minikube tunnel > tunnel.log 2>&1 &
  405  ps aux | grep minikube
  406  kubectl get svc -n ingress-nginx
  407  sudo vi /etc/hosts
  408  sudo nano /etc/hosts
  409  sudo vi /etc/hosts
  410  sudo nano /etc/hosts
  411  cat /etc/hosts
  412  kubectl get svc ingress-nginx
  413  kubectl get ingress-nginx
  414  kubectl get pods ingress-nginx
  415  vi /etc/hots
  416  ls
  417  cd go-web-app-MAIN
  418  ls
  419  cd k8
  420  ls
  421  kubectl get nodes
  422  cat deployment
  423  cat deployment.yaml
  424  kubectl delete deployment go-web-app
  425  kubectl get deployment
  426  vi deployment.yaml
  427  kubectl apply -f deployment.yaml
  428  kubectl get deployment
  429  kubectl get ing
  430  minikube ip
  431  kubectl get svc -n ingress-nginx
  432  nslookup
  433  nslookup 10.110.215.173
  434  ping 10.110.215.173
  435  ping google.com
  436  ls
  437  cd go-web-app-MAIN
  438  ls
  439  cd k8
  440  ls
  441  minikube ip
  442  ping 192.168.49.2
  443  ls
  444  cd go-web-app-MAIN
  445  cd k8
  446  ls
  447  kubectl get ing
  448  kubectl describe ing
  449  kubectl get svc
  450  kubectl get pods
  451  kubectl logs go-web-app-8688bccfc8-kf5lz
  452  kubectl logs go-web-app
  453  kubectl get pods -n ingress-nginx
  454  curl http://go-web-app.local
  455  cat ingress.yaml
  456  curl http://go-web-app.locak
  457  curl http://go-web-app.local
  458  cat /etc/hosts
  459  minikube ip
  460  vim /etc/hosts
  461  nano /etc/hosts
  462  sudo nano /etc/hosts
  463  cat /etc/hosts
  464  sudo nano /etc/hosts
  465  cat /etc/hosts
  466  curl http://go-web-app.local
  467  kubectl get ingress
  468  kubectl describe ingress go-web-app
  469  kubectl get svc go-web-app
  470  kubectl decribe svc go-web-app
  471  kubectl describe svc go-web-app
  472  kubectl get pods -o wide
  473  curl http://10.244.0.12:8080
  474  sudo curl http://10.244.0.12:8080
  475  kubectl get pods
  476  kubectl logs go-web-app-8688bccfc8-kf5lz
  477  kubectl describe pod go-web-app-8688bccfc8-kf5lz
  478  kubectl exec -it go-web-app-8688bccfc8-kf5lz --/bin/sh
  479  kubectl exec -it go-web-app-8688bccfc8-kf5lz -- /bin/sh
  480  kubectl exec -it go-web-app-8688bccfc8-kf5lz -- cat /etc/os-release
  481  sudo kubectl exec -it go-web-app-8688bccfc8-kf5lz -- cat /etc/os-release
  482  cd ..
  483  la
  484  ls
  485  docker images
  486  docker run -p 8080:8080 ramdev284/dockerfile:tag
  487  docker run -p 8080:8080 ramdev284/dockerfile
  488  sudo docker run -p 8080:8080 ramdev284/dockerfile .
  489  docker build -t newimags:latest .
  490  docker images
  491  docker run -p 8080:8080 newimage
  492  docker logout
  493  docker run -p 8080:8080 newimage
  494  sudo docker run -p 8080:8080 newimage
  495  sudo docker run -p 8080:8080 ramdev284/dockerfile
  496  docker pull ramdev284/dockerfile
  497  docker pull ramdev284/dockerfile:tag
  498  docker images
  499  docker run -p 8080:8080 ramdev284/dockerfile
  500  sudo systemctl status docker
  501  journalctl -u docker
  502  sudo yum install docker -y
  503  ls
  504  cd go-web-app-MAIN
  505  ls
  506  sudo docker ps
  507  docker images
  508  ls
  509  sudo cd k8
  510  ls
  511  cd k8
  512  ls
  513  kubectl get pods
  514  kubectl describe go-web-app-8688bccfc8-kf5lz
  515  kubectl get describe go-web-app-8688bccfc8-kf5lz
  516  kubectl describe pod go-web-app-8688bccfc8-kf5lz
  517  kubectl get svc
  518  kubectl get svc -n go-web-app
  519  kubectl exec -it go-web-app-8688bccfc8-kf5lz --curl http://go-web-app:32018
  520  kubectl exec -it go-web-app-8688bccfc8-kf5lz -- curl http://go-web-app:32018
  521  ;s
  522  ls
  523  mkdir helm—---------------> HELM
  524  cd helm
  525  sudo yum install helm -y
  526  curl -fsSL https://helm.sh/helm-signing.asc | sudo gpg --dearmor -o /usr/share/keyrings/helm.gpg
  527  sudo mkdir -p /usr/share/keyrings
  528  curl -fsSL https://helm.sh/helm-signing.asc | sudo gpg --dearmor -o /usr/share/keyrings/helm.gpg
  529  sudo curl -fsSL https://helm.sh/helm-signing.asc | sudo gpg --dearmor -o /usr/share/keyrings/helm.gpg
  530  sudo yum update -y
  531  curl -fsSL https://get.helm.sh/helm-v3.13.0-linux-amd64.tar.gz -o helm.tar.gz
  532  tar -zxvf helm.tar.gz
  533  sudo mv linux-amd64/helm /usr/local/bin/helm
  534  helm version
  535  ls
  536  cd linux-amd64
  537  ls
  538  cd ..
  539  rm -rf helm.tar.gz linux-amd64
  540  ls
  541  cd ..
  542  ls
  543  cd helm
  544  helm version
  545  helm --version
  546  helm create go-web-app-chart
  547  ls
  548  cd go-web-app-chart
  549  ls
  550  rm -rf charts
  551  ls
  552  cd templates
  553  ls
  554  rm -rf *
  555  ls
  556  cd .. ..
  557  ls
  558  cd ..
  559  ls
  560  cd ..
  561  ls
  562  cat deployment.yaml
  563  cat services.yaml
  564  cat ingress.yaml
  565  ls
  566  cd helm
  567  ls
  568  cd go-web-app-chart
  569  ls
  570  cd templates
  571  ls
  572  vim deployment.yaml
  573  vim service.yaml
  574  vim ingress.yaml
  575  vim deployment.yaml
  576  cat deployment.yaml
  577  vim deployment.yaml
  578  cat deployment.yaml
  579  vim deployment.yaml
  580  cat deployment.yaml
  581  ls
  582  cd ..
  583  ls
  584  cat values.yaml
  585  vim values.yaml
  586  cat values.yaml
  587  ls
  588  cd templates
  589  ls
  590  cd ..
  591  ls
  592  vim values.yaml
  593  cat values.yaml
  594  clear
  595  kubectl get pods
  596  kubectl all pods
  597  kubectl get all
  598  kubectl delete deploy go-web-app
  599  kubectl delete service go-web-app
  600  kubectl delete ingress go-web-app
  601  kubectl get all
  602  ls
  603  cd ..
  604  ls
  605  helm install go-web-app ./go-web-app-chart
  606  ls
  607  cd go-web-app-chart
  608  ls
  609  cat values.yaml
  610  ls
  611  cd templates
  612  ls
  613  cat deployment.yaml
  614  vim deployment.yaml
  615  kubectl get all
  616  cd ..
  617  helm install go-web-app ./go-web-app-chart
  618  kubectl get all
