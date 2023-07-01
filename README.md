# Implantação de aplicação web usando Ansible

## Introdução

Neste projeto, há a criação de uma máquina virtual (VM) através do Vagrant, que será provisionada pelo Shell e pelo Ansible.

O primeiro provisionamento ocorrerá após a leitura da linha

`config.vm.provision "shell", path: "setup.sh"`

O primeiro provisionamento realizará as seguintes tarefas:

* Adicionar o repositório oficial do Ansible através de um PPA
* Instalar o Ansible

O primeiro provisionamento trata-se de um preparo para o próximo provisionamento.

O segundo provisionamento ocorrerá após a leitura do bloco

```
config.vm.provision "ansible_local" do |ansible|
  ansible.provisioning_path = "/ansible"
  ansible.playbook = "playbook.yml"
end
```

O provisionamento feito pelo Ansible realizará a role nginx, que contém as seguintes tarefas:

* Atualizar o cache do apt
* Instalar o nginx
* Copiar os arquivos index.html e nginx.conf para o diretório /var/www/html

## Como usar este projeto

Para criar a VM, execute:

`vagrant up`

Para acessar a VM, execute:

`vagrant ssh`

Para acessar a aplicação web, digite na barra de pesquisa de um navegador web:

`192.168.56.2`

Para destruir a VM, execute:

`vagrant destroy -f`
