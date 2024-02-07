> [!Note]
> **Português BR:** <br />
> Esta nota destaca a importância de usar o Termux apenas para fins de teste e aprendizado, e enfatiza a necessidade de uma VPS para um ambiente de servidor SA-MP profissional.
>
> **English US:** <br />
> This note highlights the importance of using Termux for testing and learning purposes only, and emphasizes the need for a VPS for a professional SA-MP server environment.

**1. Vamos instalar o pacote: `nano`, `tar` e `wget`** <br />
*1. Let's install the package: `nano`, `tar` and `wget`*

```bash
apt-get install -y nano tar wget
```

**2. Vamos baixar e extrair o arquivo compactado com o samp-server:** <br />
*2. Let's download and extract the compressed file with samp-server:*

```bash
cd $HOME
wget --no-check-certificate https://gta-multiplayer.cz/downloads/samp037svr_R2-2-1.tar.gz
tar -xvf samp037svr_R2-2-1.tar.gz
cd samp03
```

**3. Precisamos editar a senha do rcon, caso contrário o servidor não iniciará:** <br />
*3. We need to edit the rcon password, otherwise the server will not start:*

> [!Tip]
> ![Editing Configuration](https://raw.githubusercontent.com/pawn-team/Termux-Tricks/main/images/Screenshot_2024-02-07-01-00-58-909_com.termux.jpg)
>
> **Português BR:** <br />
> Utilize o comando `nano server.cfg`, procure por *"rcon_password"* e escreva uma senha.
>
> **English US:** <br />
> Use the command `nano server.cfg`, search for *"rcon_password"* and write a password.

**4. Agora só precisamos iniciar o servidor:** <br />
*4. Now we just need to start the server:*

```bash
./samp03svr
```

> [!Tip]
> **Português BR:** <br />
> Utilize as teclas `CTRL + C` para encerrar o servidor. <br />
> Você pode ler os logs utilizando ocomando `cat server_log.txt`. <br />
> O ExaTermux por padrão tem uma pasta vinculada a memória interna, utilize o comando `mv` e `cp` para mover ou copiar algum arquivo de dentro para fora e vice-versa.
>
> **English US:**
> Use the `CTRL + C` keys to shut down the server. <br />
> You can read the logs using the `cat server_log.txt` command. <br />
> ExaTermux by default has a folder linked to internal memory, use the `mv` or `cp` command to move or copy a file from inside to outside and opposite too.

> [!Note]
> **Português BR:** <br />
> Esta nota destaca a obrigatoriedade do uso de um ambiente x86, você pode obtê-lo através [desse tutorial](https://github.com/pawn-team/Termux-Tricks/blob/main/install-x86-environment.md)!
>
> **English US:** <br />
> This note highlights the mandatory use of an x86 environment, you can obtain it through [this tutorial](https://github.com/pawn-team/Termux-Tricks/blob/main/install-x86-environment.md)!
