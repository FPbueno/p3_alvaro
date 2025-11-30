## Configurações do env

```
## substituir as configurações de conexão com o banco de dados pelas definidas em sua máquina
DB_USER = "postgres" 
DB_PASSWORD = 123
DB_HOST = "localhost"
DB_PORT = 5432
DB_NAME = "p3_db"
PORT = 5000
JWT_SECRET = "jwt_secret_key"
```
Para criar as tabelas necessárias, cole os comandos SQL encontrados em ./backend/initdb.sql em seu postgre após criar o banco chamado(em nosso caso) p3_db
