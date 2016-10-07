## Execute specific task

### yaml

```yml
- hosts: my_host
  become: yes
  tasks:
    - name: install vim
      yum: name=vim state=present
      tags:
       - vim 
```

### Execute

```bash
ansible-playbook my_host.yml --tags "vim"
```
