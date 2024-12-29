### Configuring the Database on Termux  
**Autor**: *DeviceBlack*  

#### 1. Updating Termux  
**Execute os seguintes comandos para garantir que o sistema esteja atualizado e o banco de dados seja instalado corretamente:**  
*Run the following commands to ensure the system is updated and the database is installed correctly:*  
```bash
pkg update && pkg upgrade -y  
pkg install mariadb -y  
```

#### 2. Initializing the Database  
**Inicialize o banco de dados e inicie o serviço:**  
*Initialize the database and start the service:*  
```bash
mariadbd --initialize  
mariadbd-safe &  
```

#### 3. Creating User  
**Entre no console do banco de dados e configure o usuário:**  
*Log into the database console and configure the user:*  
```bash
mariadb  

CREATE USER 'user'@'localhost' IDENTIFIED BY 'password';  
GRANT ALL PRIVILEGES ON *.* TO 'user'@'localhost' WITH GRANT OPTION;  
FLUSH PRIVILEGES;  
EXIT;  
```

#### 4. Creating Database  
**Conecte-se ao banco de dados com o novo usuário e configure o banco de dados e a tabela:**  
*Connect to the database with the new user and configure the database and table:*  
```bash
mariadb -u user -p  
# Digite a senha: password  
# Enter the password: password  

CREATE DATABASE test_db;  
USE test_db;  

CREATE TABLE test_table (  
    id INT AUTO_INCREMENT PRIMARY KEY,  
    name VARCHAR(100) NOT NULL,  
    age INT NOT NULL  
);  

GRANT ALL PRIVILEGES ON test_db.test_table TO 'user'@'localhost';  
FLUSH PRIVILEGES;  
EXIT;  
```

#### 5. Automating  
**Crie um script para iniciar o banco de dados automaticamente ao abrir o Termux:**  
*Create a script to start the database automatically when opening Termux:*  
```bash
echo -e "mariadbd-safe &" > $PREFIX/etc/profile.d/mariadb.sh  
```

#### 6. Restarting Termux  
**Feche e reabra o Termux. Confirme se o banco de dados está em execução:**  
*Close and reopen Termux. Confirm that the database is running:*  
```bash
ps aux | grep mariadb  
```

#### 7. Access  
**Use as seguintes credenciais para acessar o banco de dados:**  
*Use the following credentials to access the database:*  
- **HOSTNAME**: localhost  
- **USERNAME**: user  
- **PASSWORD**: password  
- **DATABASE**: test_db  

#### Observation  
**Essa configuração é útil para aprendizado ou pequenos projetos locais. Para uso em produção, considere reforçar a segurança do banco de dados.**  
*This setup is useful for learning or small local projects. For production use, consider enhancing database security.*
