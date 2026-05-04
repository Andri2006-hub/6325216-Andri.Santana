Questão 1: Arquitetura e Componentes
a) O Control Plane gerencia o cluster Kubernetes, expondo a API, agendando Pods, mantendo estado desejado e gerenciando nós. Um componente chave é o etcd, que armazena todos os dados do cluster de forma distribuída e consistente.

b) O kubelet é o principal software nos Worker Nodes, responsável por garantir que os Pods estejam rodando e saudáveis, mantendo o estado desejado.

Questão 2: O Pod
a) Um Pod pode conter múltiplos contêineres para aplicações co-localizadas que precisam compartilhar recursos de forma apertada. A principal regra é que compartilham o mesmo IP de rede e portas (namespace de rede).

b) É inadequado criar Pods diretamente em produção porque eles são efêmeros - não há gerenciamento automático de réplicas, atualizações rolling ou recuperação de falhas. Deve-se usar controladores como Deployment.

Questão 3: Manifesto YAML
Os quatro campos obrigatórios são:

apiVersion

kind

metadata

spec

Questão 4: Deployment
text
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deploy-tf09
spec:
  replicas: 3
  selector:
    matchLabels:
      app: web-tf09
  template:
    metadata:
      labels:
        app: web-tf09
    spec:
      containers:
      - name: nginx
        image: nginx:latest
        ports:
        - containerPort: 80
Questão 5: Service
text
apiVersion: v1
kind: Service
metadata:
  name: web-service-tf09
spec:
  type: NodePort
  selector:
    app: web-tf09
  ports:
  - port: 80
    targetPort: 80
    nodePort: 30000