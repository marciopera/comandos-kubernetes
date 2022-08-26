**BASH**

source <(kubectl completion bash) # configuração de autocomplete no bash do shell atual, o pacote bash-completion precisa ter sido instalado primeiro.
echo "source <(kubectl completion bash)" >> ~/.bashrc # para adicionar o autocomplete permanentemente no seu shell bash.

Você também pode usar uma abreviação para o atalho para *kubectl* que também funciona com o auto completar:

alias k=kubectl
complete -F __start_kubectl k
