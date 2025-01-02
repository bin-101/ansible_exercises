- Debian 10 以外うまく動作しなかったため、すべてDebian 10にする
- 仮想マシンの削除
```
 1975  virsh list --all
 1976  virsh shutdown ansible_exercises_marutamachi
 1977  virsh shutdown ansible_exercises_oike
 1978  virsh shutdown ansible_exercises_marutamachi
 1979  virsh shutdown ansible_exercises_oike
 1980  virsh shutdown ansible_exercises_oshikoji
 1981  virsh shutdown ansible_exercises_takeyamachi
 1982  virsh shutdown ansible_exercises_nijyo
 1983  virsh shutdown ansible_exercises_ebisugawa
 1984  virsh list --all
 1985  virsh undefine ansible_exercises_marutamachi
 1986  virsh undefine ansible_exercises_oike
 1987  virsh undefine ansible_exercises_oshikoji
 1988  virsh undefine ansible_exercises_takeyamachi
 1989  virsh undefine ansible_exercises_nijyo
 1990  virsh undefine ansible_exercises_ebisugawa
```
- libvirtのストレージプールを削除
```
bin101@bin101-Inspiron-16-5635:~/code/ansible_exercises$ virsh vol-list default
 Name                                                                   Path
----------------------------------------------------------------------------------------------------------------------------------------------------------------------
 almalinux-VAGRANTSLASH-8_vagrant_box_image_8.10.20240821_box_0.img     /var/lib/libvirt/images/almalinux-VAGRANTSLASH-8_vagrant_box_image_8.10.20240821_box_0.img
 centos-VAGRANTSLASH-7_vagrant_box_image_2004.01_box.img                /var/lib/libvirt/images/centos-VAGRANTSLASH-7_vagrant_box_image_2004.01_box.img
 centos-VAGRANTSLASH-8_vagrant_box_image_2011.0_box.img                 /var/lib/libvirt/images/centos-VAGRANTSLASH-8_vagrant_box_image_2011.0_box.img
 debian-VAGRANTSLASH-buster64_vagrant_box_image_10.20231211.1_box.img   /var/lib/libvirt/images/debian-VAGRANTSLASH-buster64_vagrant_box_image_10.20231211.1_box.img

bin101@bin101-Inspiron-16-5635:~/code/ansible_exercises$ virsh vol-delete almalinux-VAGRANTSLASH-8_vagrant_box_image_8.10.20240821_box_0.img --pool default
virsh vol-delete centos-VAGRANTSLASH-7_vagrant_box_image_2004.01_box.img --pool default
virsh vol-delete centos-VAGRANTSLASH-8_vagrant_box_image_2011.0_box.img --pool default
virsh vol-delete debian-VAGRANTSLASH-buster64_vagrant_box_image_10.20231211.1_box.img --pool default
Vol almalinux-VAGRANTSLASH-8_vagrant_box_image_8.10.20240821_box_0.img deleted

Vol centos-VAGRANTSLASH-7_vagrant_box_image_2004.01_box.img deleted

Vol centos-VAGRANTSLASH-8_vagrant_box_image_2011.0_box.img deleted

Vol debian-VAGRANTSLASH-buster64_vagrant_box_image_10.20231211.1_box.img deleted
```
- 鍵の登録し直し
```
ssh-keygen -f "/home/bin101/.ssh/known_hosts" -R "192.168.111.101"
ssh-copy-id -i ~/.ssh/id_ed25519.pub vagrant@192.168.111.101 # 各サーバーに対して行う
```