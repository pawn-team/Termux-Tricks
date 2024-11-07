# Exagear For Termux

> [!Note]
> **Português BR:** <br />
> Versão modificada não oficial do Exagear para Termux e ambientes baseados em proot. <br />
> O objetivo principal do projeto é alcançar a possibilidade de um ambiente estável e rápido.
>
> **English U.S:** <br />
> Unofficial modified version of Exagear for Termux and proot-based environments. <br />
> The main objective of the project is to achieve the possibility of a stable and fast environment.


## Installation Process

**1. Instale `tar`, `wget` e `git` usando um gerenciador de pacotes:** <br />
*1. Install `tar`, `wget` and `git` using a package manager:*

```bash
yes | pkg upd -y && yes | pkg upg -y
pkg install -y tar git wget
termux-setup-storage
```

**2. Clone o repositório do [ZhymabekRoman](https://github.com/ZhymabekRoman) no diretório inicial:** <br />
*2. Clone the ZhymabekRoman repository in your home directory:*

```bash
git clone https://github.com/ZhymabekRoman/Exagear-For-Termux $HOME/ExaTermux --recurse-submodules
```

**3. Agora vamos entrar na pasta** <br />
*3. Now let's go into the folder*

```bash
cd $HOME/ExaTermux
```

**4. Agora você precisa extrair qualquer arquivo rootfs da distribuição para a pasta `exagear-fs`.** <br />
*4. Now you need to extract any rootfs file from the distribution to the `exagear-fs` folder.* <br />

```bash
wget "https://github.com/termux/proot-distro/releases/download/v4.7.0/debian-bookworm-i686-pd-v4.7.0.tar.xz"
tar --warning=no-unknown-keyword --delay-directory-restore --preserve-permissions -xvf debian-bookworm-i686-pd-v4.7.0.tar.xz --exclude='dev'||:
mv debian-bookworm-i686 exagear-fs
```

**5. E enfim, vamos inicializar o exagear:** <br />
*5. And finally, let's initialize exagear:*

```bash
./start-exagear.sh login
```

> [!Tip]
> **Português BR:** <br />
> Você precisará atualizar os pacotes assim que logar pela primeira vez, então recomendo que use esses comandos abaixo!
>
> **English US:** <br />
> You will need to update the packages as soon as you log in for the first time, so I recommend using these commands below!
>
> ```bash
> apt-get update
> echo -e "cd $HOME\nexport DEBIAN_FRONTEND=noninteractive\nalias ls='ls --color=auto'\nln -s /storage/emulated/0/ /sdcard &> /dev/null" > /etc/profile.d/fixes.sh
> bash /etc/profile.d/fixes.sh
> ```
