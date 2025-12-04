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

Foi aplicado singleton na conexão com o banco de dados, no arquivo db.ts
```
class Database {
  private static instance: Pool;

  private constructor() {} // impede new Database()

  static getInstance(): Pool {
    if (!Database.instance) {
      console.log("Criando nova instância do Pool...");
      Database.instance = new Pool({
        user: process.env.DB_USER,
        password: process.env.DB_PASSWORD,
        host: process.env.DB_HOST,
        port: Number(process.env.DB_PORT),
        database: process.env.DB_NAME,
      });
    }

    return Database.instance;
  }
}

export default Database;
```

E depois carregando desta forma:
```
import Database from '../db';

const pool = Database.getInstance();
```