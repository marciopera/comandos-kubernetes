# Atualizando Recursos

**Aplica o rollout nos containers "www" do deployment "frontend", atualizando a imagem.**
```
kubectl set image deployment/frontend www=image:v2
```

**Verifica o histórico do deployment, incluindo a revisão.**
```
kubectl rollout history deployment/frontend
```

**Rollback para o deployment anterior.**
```
kubectl rollout undo deployment/frontend
```

**Rollback para uma revisão específica.**
```
kubectl rollout undo deployment/frontend --to-revision=2
```

**Acompanhe o status de atualização do "frontend" até sua conclusão sem interrupção.**
```
kubectl rollout status -w deployment/frontend
```

**Reinício contínuo do deployment "frontend.**
```
kubectl rollout restart deployment/frontend 
```

**Atualização contínua dos pods de frontend-v1.**
```
kubectl rolling-update frontend-v1 -f frontend-v2.json
```

**Altera o nome do recurso e atualiza a imagem.**
```
kubectl rolling-update frontend-v1 frontend-v2 --image=image:v2
```

**Atualize a imagem dos pods do frontend.**
```
kubectl rolling-update frontend --image=image:v2
```

**Interromper o lançamento existente em andamento.**
```
kubectl rolling-update frontend-v1 frontend-v2 --rollback
```

**Substitua um pod com base no JSON passado para std.**
```
cat pod.json | kubectl replace -f -
```

**Força a substituição, exclui e recria o recurso. Causará uma interrupção do serviço.**
```
kubectl replace --force -f ./pod.json
```

**Crie um serviço para um nginx replicado, que serve na porta 80 e se conecta aos contêineres na porta 8000.**
```
kubectl expose rc nginx --port=80 --target-port=8000
```

**Atualizar a versão da imagem (tag) de um pod de contêiner único para a v4.**
```
kubectl get pod mypod -o yaml | sed 's/\(image: myimage\):.*$/\1:v4/' | kubectl replace -f -
```

**Adicionar uma label.**
```
kubectl label pods my-pod new-label=awesome
```

**Adicionar uma anotação.**
```
kubectl annotate pods my-pod icon-url=http://goo.gl/XXBTWq
```

**Escalar automaticamente um deployment "foo".**
```
kubectl autoscale deployment foo --min=2 --max=10
```
