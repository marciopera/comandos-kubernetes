# Contexto e Configuração do Kubectl.

Defina com qual cluster Kubernetes o kubectl se comunica e modifique os detalhes da configuração. 

Consulte a documentação [Autenticando entre clusters com o kubeconfig](https://kubernetes.io/docs/tasks/access-application-cluster/configure-access-multiple-clusters/) para informações detalhadas do arquivo de configuração.


**Exibr configurações do kubeconfig mergeadas.**

```
kubectl config view
```

**Use vários arquivos kubeconfig ao mesmo tempo e visualize a configuração mergeada.**

```
KUBECONFIG=~/.kube/config:~/.kube/kubconfig2 
```

**Obtenha a senha para o usuário e2e.**
```
kubectl config view -o jsonpath='{.users[?(@.name == "e2e")].user.password}' 
```
**Exibir o primeiro usuário.**
```
kubectl config view -o jsonpath='{.users[].name}'    
```
**Obtendo uma lista de usuários.**
```
kubectl config view -o jsonpath='{.users[*].name}'   
```
 **Exibir lista de contextos.**
``` 
kubectl config get-contexts                         
```
**Exibir o contexto atual.**
```
kubectl config current-context                       
```
**Defina o contexto padrão como _my-cluster-name_.**
```
kubectl config use-context my-cluster-name           
```

**Adicione um novo cluster ao seu kubeconfig que suporte autenticação básica.**
```
kubectl config set-credentials kubeuser/foo.kubernetes.com --username=kubeuser --password=kubepassword
```
**Salve o namespace permanentemente para todos os comandos subsequentes do kubectl nesse contexto.**
```
kubectl config set-context --current --namespace=ggckad-s2
```
**Defina um contexto utilizando um nome de usuário e o namespace.**
```
kubectl config set-context gce --user=cluster-admin --namespace=foo \  && kubectl config use-context gce
```
**Excluir usuário foo.**
```
kubectl config unset users.foo
```

