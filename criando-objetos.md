# Criando objetos

Manifestos Kubernetes podem ser definidos em YAML ou JSON. As extensões de arquivos _.yaml_, _.yml_, e _.json_ podem ser usadas.

# criar recurso(s)

kubectl apply -f ./my-manifest.yaml   

# criar a partir de vários arquivos
kubectl apply -f ./my1.yaml -f ./my2.yaml 
 # criar recurso(s) em todos os arquivos de manifesto no diretório
    kubectl apply -f ./dir  
# criar recurso(s) a partir de URL

   
 # iniciar uma única instância do nginx
kubectl apply -f https://git.io/vPieo          
kubectl create deployment nginx --image=nginx 
kubectl explain pods,svc                       # obtenha a documentação de manifesto do pod
