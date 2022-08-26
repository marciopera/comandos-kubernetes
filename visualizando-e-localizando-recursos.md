# Visualizando e Localizando Recursos

**Listar todos os serviços do namespace.**
```
kubectl get services
```
**Listar todos os pods em todos namespaces.**
```
kubectl get pods --all-namespaces
```
**Listar todos os pods no namespace atual, com mais detalhes.**
```
kubectl get pods -o wide
```
**Listar um deployment específico.**
```
kubectl get deployment my-dep
```
**Listar todos os pods no namespace.**
```
kubectl get pods
```
**Obter o YAML de um pod.**
```
kubectl get pod my-pod -o yaml
```
**Descrever comandos com saída detalhada.**
```
kubectl describe nodes my-node
kubectl describe pods my-pod
```
**Listar serviços classificados por nome.**
```
kubectl get services --sort-by=.metadata.name
``` 
**Listar pods classificados por contagem de reinicializações.**
```
kubectl get pods --sort-by='.status.containerStatuses[0].restartCount'
```
**Listar PersistentVolumes classificado por capacidade.**
```
kubectl get pv --sort-by=.spec.capacity.storage
``` 
**Obtenha a versão da label de todos os pods com a label app=cassandra.**
```
kubectl get pods --selector=app=cassandra -o \
  jsonpath='{.items[*].metadata.labels.version}'
```
**Obter todos os nós workers (use um seletor para excluir resultados que possuem uma label nomeado 'node-role.kubernetes.io/master').**
```
kubectl get node --selector='!node-role.kubernetes.io/master'
``` 
**Obter todos os pods em execução no namespace.**
```
kubectl get pods --field-selector=status.phase=Running
```
**Obter ExternalIPs de todos os nós.**
```
kubectl get nodes -o jsonpath='{.items[*].status.addresses[?(@.type=="ExternalIP")].address}'
``` 
**Listar nomes de pods pertencentes a um RC particular.**
**O comando "jq" é útil para transformações que são muito complexas para jsonpath, pode ser encontrado em https://stedolan.github.io/jq/.**
```
sel=${$(kubectl get rc my-rc --output=json | jq -j '.spec.selector | to_entries | .[] | "\(.key)=\(.value),"')%?}
echo $(kubectl get pods --selector=$sel --output=jsonpath={.items..metadata.name})
```
**Mostrar marcadores para todos os pods(ou qualquer outro objeto Kubernetes que suporte rotulagem).**
```
kubectl get pods --show-labels
``` 
**Verifique quais nós estão prontos.**
```
JSONPATH='{range .items[*]}{@.metadata.name}:{range @.status.conditions[*]}{@.type}={@.status};{end}{end}' \
 && kubectl get nodes -o jsonpath="$JSONPATH" | grep "Ready=True"
```
**Listar todos os segredos atualmente em uso por um pod.**
```
kubectl get pods -o json | jq '.items[].spec.containers[].env[]?.valueFrom.secretKeyRef.name' | grep -v null | sort | uniq
``` 
**Listar todos os containerIDs de initContainer de todos os pods.**
**Útil ao limpar contêineres parados, evitando a remoção de initContainers.**
```
kubectl get pods --all-namespaces -o jsonpath='{range .items[*].status.initContainerStatuses[*]}{.containerID}{"\n"}{end}' | cut -d/ -f3
```
**Listar eventos classificados por timestamp.**
```
kubectl get events --sort-by=.metadata.creationTimestamp
``` 
**Compara o estado atual do cluster com o estado em que o cluster estaria se o manifesto fosse aplicado.**
```
kubectl diff -f ./my-manifest.yaml
``` 
