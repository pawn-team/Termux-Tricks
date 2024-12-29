### Tutorial: Configurando banco de dados no Termux  
**Autor**: DeviceBlack

#### 1. Atualizando e Preparando o Termux  
Execute os seguintes comandos para garantir que o sistema esteja atualizado e o MariaDB seja instalado corretamente:  
```bash
pkg update && pkg upgrade -y
pkg install mariadb -y
```

#### 2. Inicializando o MariaDB  
Inicialize o banco de dados do MariaDB e inicie o serviço:  
```bash
mariadbd --initialize
mariadbd-safe &
```

#### 3. Criando o Usuário e Concedendo Permissões  
Entre no console do MariaDB e configure o usuário:  
```bash
mariadb

CREATE USER 'eu_mesmo'@'localhost' IDENTIFIED BY 'minha_senha';
GRANT ALL PRIVILEGES ON *.* TO 'eu_mesmo'@'localhost' WITH GRANT OPTION;
FLUSH PRIVILEGES;
EXIT;
```

#### 4. Criando um Banco de Dados e uma Tabela  
Conecte-se ao MariaDB com o novo usuário e configure o banco de dados e a tabela:  
```bash
mariadb -u eu_mesmo -p
# Digite a senha: minha_senha

CREATE DATABASE meu_banco;
USE meu_banco;

CREATE TABLE minha_tabela (
    id INT AUTO_INCREMENT PRIMARY KEY,
    nome VARCHAR(100) NOT NULL,
    idade INT NOT NULL
);

GRANT ALL PRIVILEGES ON meu_banco.minha_tabela TO 'eu_mesmo'@'localhost';
FLUSH PRIVILEGES;
EXIT;
```

#### 5. Automatizando o MariaDB no Termux  
Crie um script para iniciar o MariaDB automaticamente ao abrir o Termux:  
```bash
echo -e "mariadbd-safe &" > $PREFIX/etc/profile.d/mariadb.sh
```

#### 6. Reinicie o Termux  
Feche e reabra o Termux. Confirme se o MariaDB está em execução:  
```bash
ps aux | grep mariadb
```

#### 7. Informações de Acesso  
Após a configuração, use as seguintes credenciais para acessar o banco:  
- **HOSTNAME**: localhost  
- **USERNAME**: eu_mesmo  
- **PASSWORD**: minha_senha  
- **DATABASE**: meu_banco  

#### Observação  
Essa configuração é útil para aprendizado ou pequenos projetos locais. Para uso em produção, considere reforçar a segurança do banco de dados.
