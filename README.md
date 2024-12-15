# Post-Install-Debian12

## Configurações Básicas

Atualize o Sistema
```
apt update ; apt upgrade -y
```
Atualize o kernel do Linux
```
apt install linux-image-amd64 linux-headers-amd64 -t bookworm-backports
```

Atualizando o firmware do seu processador
```
apt install intel-microcode
```

Remova pacotes desnecessários, neste caso vamos remover os jogos e o pidgin, mas se vc usa estes aplicativos então pule esta etapa.
```
apt remove pidgin gnome-games --purge && apt autoremove
```

Habilitando os botões de Maximizar e Minimizar
```
# Saia do Root para executar o comando!!!
gsettings set org.gnome.desktop.wm.preferences button-layout ':minimize,maximize,close'
```

Configuração da sources.list 
```
nano /etc/apt/sources.list
```
```
deb http://deb.debian.org/debian/ bookworm main contrib non-free non-free-firmware
deb http://security.debian.org/debian-security bookworm-security main contrib non-free non-free-firmware
deb http://deb.debian.org/debian bookworm-updates main contrib non-free non-free-firmware
```

Alterando o valor da swappiness
```
nano /etc/sysctl.conf
```
```
vm.swappiness=10
```

Adicione seu usuário ao grupo sudo
```
apt install sudo
```
```
adduser seu_usuario sudo
```

Instale os pacotes de fontes da Micro$oft
```
apt install ttf-mscorefonts-installer && fc-cache -f -v
```

Ativando o firewall
```
apt install ufw gufw
```
```
ufw enable
```

extração e compactação de arquivos
```
apt install arc arj cabextract lhasa p7zip p7zip-full p7zip-rar rar unrar unace unzip xz-utils zip
```

Flatpak
```
apt install flatpak
```
```
apt install gnome-software-plugin-flatpak
```
```
flatpak remote-add --if-not-exists flathub https://dl.flathub.org/repo/flathub.flatpakrepo
```

Removendo libreoffice e firefox-esr
```
apt remove libreoffice* ; apt remove firefox-esr*
```

Git
```
apt install git
```
```
$ git config --global user.name "Nome de Usuário"
$ git config --global user.email Email
```
  SSH: https://docs.github.com/pt/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent

Java
```
apt install openjdk-17-jdk ; apt install openjdk-17-jre
```
Definir a variável de ambiente JAVA_HOME
```
sudo nano /etc/environment
```
```
JAVA_HOME="/usr/lib/jvm/java-17-openjdk-amd64"
```

Ruby
```
apt install ruby-full
```

Vagrant
https://developer.hashicorp.com/vagrant/install

Ansible
https://docs.ansible.com/ansible/latest/installation_guide/installation_distros.html

Docker
https://docs.docker.com/engine/install/debian/

Kubernetes
https://kubernetes.io/docs/setup/production-environment/tools/kubeadm/install-kubeadm/
