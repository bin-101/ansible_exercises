- sudo vi /etc/apt/sources.list
    - buster-backportsが入っているものをコメントアウト
```
vagrant@marutamachi:~$ sudo lsof /var/lib/dpkg/lock-frontend
COMMAND  PID USER   FD   TYPE DEVICE SIZE/OFF   NODE NAME
apt     2611 root    4uW  REG  254,1        0 655487 /var/lib/dpkg/lock-frontend
vagrant@marutamachi:~$ sudo kill 2611
vagrant@marutamachi:~$ sudo dpkg --configure -a
```
- ansibleを実行
```
(ansible_exercises) bin101@bin101-Inspiron-16-5635:~/code/ansible_exercises/sec8$ ansible-playbook -i hosts.yml nginx.yml

PLAY [Install Nginx] ************************************************************************************************************************

TASK [Gathering Facts] **********************************************************************************************************************
ok: [marutamachi]

TASK [Ensure apt cache is up-to-date] *******************************************************************************************************
ok: [marutamachi]

TASK [Install Nginx] ************************************************************************************************************************
changed: [marutamachi]

TASK [Ensure Nginx is started and enabled] **************************************************************************************************
ok: [marutamachi]

PLAY RECAP **********************************************************************************************************************************
marutamachi                : ok=4    changed=1    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
```
- 192.168.111.101:80でnginxが開くことを確認