# BASH
 
**Configuração de autocomplete no bash do shell atual, o pacote bash-completion precisa ter sido instalado primeiro.**
```
source <(kubectl completion bash)
```
 
**Para adicionar o autocomplete permanentemente no seu shell bash.**
```
echo "source <(kubectl completion bash)" >> ~/.bashrc
```
Você também pode usar uma abreviação para o atalho para *kubectl* que também funciona com o auto completar:
```
alias k=kubectl
complete -F __start_kubectl k
```

# ZSH

**Configuração para usar autocomplete no terminal zsh no shell atual**
```
source <(kubectl completion zsh)
```

**Adicionar auto completar permanentemente para o seu shell zsh**
```
echo "if [ $commands[kubectl] ]; then source <(kubectl completion zsh); fi"
```
