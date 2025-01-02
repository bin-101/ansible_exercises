```
(ansible_exercises) bin101@bin101-Inspiron-16-5635:~/code/ansible_exercises/sec6$ ansible-inventory -i hosts5.yml --list --yaml
all:
  children:
    db:
      hosts:
        marutamachi:
          ansible_host: 192.168.111.101
          ansible_ssh_private_key_file: ~/.ssh/id_ed25519
          ansible_user: vagrant
          db_password: tiger
          db_port: 1521
          db_user: scott
        takeyamachi:
          ansible_host: 192.168.111.102
          ansible_ssh_private_key_file: ~/.ssh/id_ed25519
          ansible_user: vagrant
          db_password: tiger
          db_port: 1521
          db_user: scott
    ungrouped:
      hosts:
        ebisugawa:
          ansible_host: 192.168.111.103
          ansible_python_interpreter: /usr/bin/python3
          ansible_ssh_private_key_file: ~/.ssh/id_ed25519
          ansible_user: vagrant
        nijyo:
          ansible_host: 192.168.111.104
          ansible_python_interpreter: /usr/bin/python3
          ansible_ssh_private_key_file: ~/.ssh/id_ed25519
          ansible_user: vagrant
        oike:
          ansible_host: 192.168.111.106
          ansible_python_interpreter: /usr/libexec/platform-python
          ansible_ssh_private_key_file: ~/.ssh/id_ed25519
          ansible_user: vagrant
        oshikoji:
          ansible_host: 192.168.111.105
          ansible_python_interpreter: /usr/bin/python3
          ansible_ssh_private_key_file: ~/.ssh/id_ed25519
          ansible_user: vagrant
```