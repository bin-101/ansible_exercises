- question1
```
(ansible_exercises) bin101@bin101-Inspiron-16-5635:~/code/ansible_exercises/sec7$ ansible db -i hosts6.yml -m ansible.builtin.command -a "hostname"
takeyamachi | CHANGED | rc=0 >>
takeyamachi
marutamachi | CHANGED | rc=0 >>
marutamachi
```
- question2
```
(ansible_exercises) bin101@bin101-Inspiron-16-5635:~/code/ansible_exercises/sec7$ ansible all -i hosts6.yml -m ansible.builtin.ping
marutamachi | SUCCESS => {
    "changed": false,
    "ping": "pong"
}
ebisugawa | SUCCESS => {
    "changed": false,
    "ping": "pong"
}
oshikoji | SUCCESS => {
    "changed": false,
    "ping": "pong"
}
nijyo | SUCCESS => {
    "changed": false,
    "ping": "pong"
}
oike | SUCCESS => {
    "changed": false,
    "ping": "pong"
}
takeyamachi | SUCCESS => {
    "changed": false,
    "ping": "pong"
}
```
- question3
```
(ansible_exercises) bin101@bin101-Inspiron-16-5635:~/code/ansible_exercises/sec7$ ansible all -i hosts6.yml -m ansible.builtin.command -a "hostname"
node1 | CHANGED | rc=0 >>
marutamachi
node3 | CHANGED | rc=0 >>
ebisugawa
node4 | CHANGED | rc=0 >>
nijyo
node6 | CHANGED | rc=0 >>
oike
node5 | CHANGED | rc=0 >>
oshikoji
node2 | CHANGED | rc=0 >>
takeyamachi
```