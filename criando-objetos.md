# Criando objetos

Manifestos Kubernetes podem ser definidos em YAML ou JSON. As extensões de arquivos _.yaml_, _.yml_, e _.json_ podem ser usadas.

**Criar recurso(s).**
```
kubectl apply -f ./my-manifest.yaml   
```
**Criar a partir de vários arquivos.**
```
kubectl apply -f ./my1.yaml -f ./my2.yaml 
```
**Criar recurso(s) em todos os arquivos de manifesto no diretório.**
```
kubectl apply -f ./dir  
```
**Criar recurso(s) a partir de URL.**
```
kubectl apply -f https://git.io/vPieo
  ``` 
**Iniciar uma única instância do nginx.**
 ```
kubectl create deployment nginx --image=nginx 
```
**Obtenha a documentação de manifesto do pod.**
 ```
kubectl explain pods,svc
```
