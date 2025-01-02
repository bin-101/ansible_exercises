以下を実行
```
ansible all -i ../prob1/hosts.yml -m ansible.builtin.command -a "cat /etc/passwd" > passwd.txt
ansible all -i ../prob1/hosts.yml -m ansible.builtin.command -a "cat /etc/shadow" -b > shadow.txt
```