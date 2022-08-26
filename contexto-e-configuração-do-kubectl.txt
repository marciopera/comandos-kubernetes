# Contexto e Configuração do Kubectl

Defina com qual cluster Kubernetes o kubectl se comunica e modifique os detalhes da configuração. 

Consulte a documentação [Autenticando entre clusters com o kubeconfig](https://kubernetes.io/docs/tasks/access-application-cluster/configure-access-multiple-clusters/) para informações detalhadas do arquivo de configuração.


**Exibr configurações do kubeconfig mergeadas.**

kubectl config view

**use vários arquivos kubeconfig ao mesmo tempo e visualize a configuração mergeada**

KUBECONFIG=~/.kube/config:~/.kube/kubconfig2 




kubectl config view -o jsonpath='{.users[?(@.name == "e2e")].user.password}' **# obtenha a senha para o usuário e2e**

kubectl config view -o jsonpath='{.users[].name}'    **# exibir o primeiro usuário**

kubectl config view -o jsonpath='{.users[*].name}'   **# obtenha uma lista de usuários**

kubectl config get-contexts                          **# exibir lista de contextos**

kubectl config current-context                       **# exibir o contexto atual**

kubectl config use-context my-cluster-name           **# defina o contexto padrão como my-cluster-name**
