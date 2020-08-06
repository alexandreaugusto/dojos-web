# 0 - Termos

A lista a seguir contém uma rápida visão geral dos termos mais relevantes usados pelo Ansible:

*Control Node:* a máquina em que o Ansible está instalado, responsável pela execução do provisionamento nos servidores que você está gerenciando.

*Inventory:* um arquivo INI que contém informações sobre os servidores que você está gerenciando.

*Playbook:* um arquivo YAML contendo uma série de procedimentos que devem ser automatizados.

*Task:* um bloco que define um único procedimento a ser executado, por exemplo: instalar um pacote.

*Module:* um módulo normalmente abstrai uma tarefa do sistema, como lidar com pacotes ou criar e alterar arquivos. O Ansible possui diversos módulos integrados, mas você também pode criar módulos personalizados.

*Role:* um conjunto de playbooks, modelos e outros arquivos relacionados, organizados de maneira predefinida para facilitar a reutilização e o compartilhamento.

*Facts:* variáveis globais que contêm informações sobre o sistema, como interfaces de rede ou sistema operacional.

*Handlers:* usado para acionar alterações no status do serviço, como reiniciar ou recarregar um serviço.

# 1 - Primeiros passos

- Inventário: (criar arquivo ./hosts)
```
goiatins.cptec.inpe.br
cajapio.cptec.inpe.br
```

- Execução como argumento:
```
ansible -i hosts all -a "/bin/echo hello"
```

- Módulos: 
```
ansible -i hosts all -m ping
ansible -i hosts all -m copy -a "src=/etc/hosts dest=/tmp/hosts"
ansible -i hosts all -m setup
ansible -i hosts all -m debug -a "msg={{ ansible_memtotal_mb }}"
```

- Execução como superusuário (default: sudo)
```
ansible -i hosts all -m ping -u luiz.coura -b -k -K
ansible -i hosts all -m apt -a "name=vim state=present" -u luiz.coura -b -k -K
ansible -i hosts all -m service -a "name=cron state=started" -u luiz.coura -b -k -K
ansible -i hosts all -m service -a "name=cron state=restarted" -u luiz.coura -b -k -K
ansible -i hosts all -l cajapio.cptec.inpe.br -a "/sbin/reboot" -u luiz.coura -b -k -K
```

# 2 - Playbook

Exemplo:
```
---
- hosts: all

  tasks:
    - name: ping
      ping:

    - name: copy
      copy:
        src: /etc/hosts
        dest: /tmp/hosts
```

# Referências:

- https://docs.ansible.com/ansible/latest/user_guide/index.html
- https://docs.ansible.com/ansible/latest/modules/list_of_all_modules.html#all-modules
- https://www.digitalocean.com/community/tutorials/configuration-management-101-writing-ansible-playbooks-pt
