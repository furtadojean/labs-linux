# labs-linux

# Como usar linux dentro dos labs da USP?
- Pré-requisitos
    - Ter o [VirtualBox](https://www.virtualbox.org/wiki/Downloads) instalado (ou usar um pc de um lab, que já possui)
    - Ter um pen drive com memória suficiente (~8GB)


## Maneira 1 - Normal [Clique para o passo-a-passo](#1)
1. Baixar a imagem de uma distribuição que goste
3. Criar uma nova máquina virtual no VirtualBox, selecionando a opção de criar um disco rígido virtual
4. Adicionar a imagem do sistema como optical drive

![debian_neofetch.png](/images/debian_neofetch.png)

## Maneira 2 - Fácil [Clique para o passo-a-passo](#2)
- Existem sites que oferecem VDIs (Virtual Disk Image) prontas com distribuições Linux. Mas precisa ter confiança na fonte
1. Baixar a VDI
2. Criar uma nova máquina virtual no VirtualBox, selecionando a opção de usar um disco rígido virtual existente

![fedora_neofetch.png](/images/fedora_neofetch.png)

## Maneira 3 - A partir de um pen drive [Clique para o passo-a-passo](#3)
1. Instalar a distribuição em um pen drive
2. Criar algum tipo de partição de permanência para salvar arquivos
3. Criar uma imagem do pen drive e convertê-la para VDI
4. Criar uma nova máquina virtual no VirtualBox, selecionando a opção de usar um disco rígido virtual existente

![tails_neofetch.png](/images/tails_neofetch.png)


## 1
- Nesse exemplo, usarei o [Debian](https://www.debian.org/download). Porém, uma versão de instalação [offline](https://cdimage.debian.org/debian-cd/current/amd64/iso-dvd/debian-11.2.0-amd64-DVD-1.iso) para não necessitar de uma conexão à internet durante a instalação

![debian_download.png](/images/debian_download.png)

- Durante a criação de uma nova máquina no VirtualBox, selecione uma pasta dentro do seu pen drive, pois o arquivo .vdi será colocado lá

![vm_folder.png](/images/vm_folder.png)

![vm_hd.png](/images/vm_hd.png)

- Com a máquina criada, clique com o botão direito e entre em configurações, onde, dentro da opção de armazenamento, você irá adicionar a imagem da distribuição Linux como um disco óptico

![optical_drive.png](/images/optical_drive.png)

![iso_attachment.png](/images/iso_attachment.png)

- Inicie a máquina e realize a instalação que, dependendo da distribuição, será bem simples. Pode demorar

![debian_install.png](/images/debian_install.png)

- Dentro da parte de particionamento de disco, não há problema em utilizar o disco inteiro, já que se trata de uma VM e não apagará nenhum dado da sua máquina real
- Instale a DE que preferir (não é uma decisão muito importante agora)
- Após instalado, confira se a imagem que foi usada para instalação foi removida

![debian_installation_complete.png](/images/debian_installation_complete.png)

![no_iso_attached.png](/images/no_iso_attached.png)

- Reinicie

![debian_login.png](/images/debian_login.png)

- Como usei a versão offline, foi preciso habilitar os repositórios para poder baixar pacotes

![main_repository.png](/images/main_repository.png)

- Se o VirtualBox não permite mudar o tamanho da tela, normalmente é possível fazer isso dentro das configurações do sistema, mesmo lugar no qual se encontram personalização de tema e outras configurações relevantes
- Para usar dentro dos labs, todo vez que se logar, insira o pen drive, abra o VirtualBox e adicione a sua máquina, que está salva no pen drive

## 2
- Escolha um site e uma distribuição e faça o download. Guarde em um pen drive

![osboxes_fedora.png](/images/osboxes_fedora.png)

![fedora_download.png](/images/fedora_download.png)

- Verifique qual é o usuário e a senha padrão já colocados

![fedora_info.png](/images/fedora_info.png)

- Dentro do lab, insira o pen drive, crie uma nova máquina virtual no VirtualBox, e selecione a distribuição baixada como disco virtual

![fedora_vm.png](/images/fedora_vm.png)

![fedora_vdi.png](/images/fedora_vdi.png)

## 3
- Essa é uma opção para quem já tem um sistema no pen drive e quer copia-lo para usar no VirtualBox. Tentar configurar para bootar direto do pen drive no VirtualBox, ou instalar o VMware - que possui acesso a essa funcionalidade mais facilmente - nos labs são alternativas que requerem direitos de administrador
1. No meu caso, usei o [Tails](https://tails.boum.org/), que já possui a opção de criar uma partição persistente e criptografada. Para rodar ele dessa forma, é necessário teclar tab na inicialização e deletar a entrada "live-media=removable"

![tails_partitions.png](/images/tails_partitions.png)

![tails_config.png](/images/tails_config.png)

2. Porém, outros métodos incluem criar uma nova partição com o espaço que sobrou no pen drive e salvar arquivos importantes nela;

![partitioning.png](/images/partitioning.png)

3. ou usar algum programa para criação de pen drives bootaveis que possua essa funcionalidade, como o Rufus (caso ainda não tenha o sistema no pen drive)
- Para criar uma imagem a partir do pen drive, o gnome-disks no linux pode ser usado. Para Windows, aparentemente, há vários programas que fazem o mesmo

![create_disk_image.png](/images/create_disk_image.png)

- Para converter a imagem do pen drive para .vdi, insira o comando (alterando para os nomes dos seus arquivos). É interessante guardar o .vdi em um pen drive para levar à universidade
    - vboxmanage convertdd sua_imagem.img novo_disco.vdi
    - Dentro do Windows, o caminho completo do programa precisa ser escrito (usualmente C:\Program Files\Oracle\VirtualBox\vboxmanage)

![vboxmanage_command.png](/images/vboxmanage_command.png)

- Dentro do lab, insira o pen drive, crie uma nova máquina no VirtualBox e selecione para usar o .vdi criado

![usb_vdi.png](/images/usb_vdi.png)
