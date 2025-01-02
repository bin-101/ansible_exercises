- ansibleの実行環境
```
bin101@bin101-Inspiron-16-5635:~/code/ansible_exercises$ python3 -m venv ansible_exercises
bin101@bin101-Inspiron-16-5635:~/code/ansible_exercises/sec4$ source ansible_exercises/bin/activate
(ansible_exercises) bin101@bin101-Inspiron-16-5635:~/code/ansible_exercises/sec4$ pip install ansible
```
- 仮想マシンの削除
```
vagrant destroy marutamachi
VBoxManage list vms
VBoxManage unregistervm "marutamachi" --delete
VBoxManage controlvm "ansible_exercises_default_1735736659595_90773" poweroff
```

- 仮想マシンの起動
```
bin101@bin101-Inspiron-16-5635:~/code/ansible_exercises$ virsh list --all
bin101@bin101-Inspiron-16-5635:~/code/ansible_exercises$ virsh net-start ansible_exercises0
bin101@bin101-Inspiron-16-5635:~/code/ansible_exercises$ virsh start ansible_exercises_marutamachi
```
- libvirtをインストール
```
sudo apt update
sudo apt install -y libvirt-daemon libvirt-daemon-system libvirt-clients qemu-kvm
sudo systemctl status libvirtd
```

- Ubuntuの仮想マシンが起動に失敗するため、ebisugawaとnijyoをDebian 10に変更した

## VirtualBox 7.0のインストール方法
- gptの解答をそのままコピペ。うまく実行できた。
はい、VirtualBox 6.1.50は古いバージョンですね。Ubuntu上で最新版のVirtualBox 7.0をインストールする手順を説明します：

1. まず、古いバージョンを削除します：
```bash
sudo apt remove virtualbox virtualbox-*
sudo apt autoremove
```

2. 必要なパッケージをインストール：
```bash
sudo apt update
sudo apt install wget apt-transport-https gnupg2 software-properties-common -y
```

3. VirtualBoxの公式リポジトリの鍵を追加：
```bash
wget -O- https://www.virtualbox.org/download/oracle_vbox_2016.asc | sudo gpg --dearmor --yes --output /usr/share/keyrings/oracle-virtualbox-2016.gpg
```

4. VirtualBoxのリポジトリを追加：
```bash
echo "deb [arch=amd64 signed-by=/usr/share/keyrings/oracle-virtualbox-2016.gpg] https://download.virtualbox.org/virtualbox/debian $(lsb_release -cs) contrib" | sudo tee /etc/apt/sources.list.d/virtualbox.list
```

5. パッケージリストを更新してVirtualBox 7.0をインストール：
```bash
sudo apt update
sudo apt install virtualbox-7.0
```