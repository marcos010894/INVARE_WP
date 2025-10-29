# WordPress com Docker

Este projeto contém a configuração Docker para rodar WordPress com MySQL.

## 📋 Pré-requisitos

- Docker instalado
- Docker Compose instalado

## 🚀 Como usar

### Iniciar os containers:
```bash
docker-compose up -d
```

### Parar os containers:
```bash
docker-compose down
```

### Ver logs:
```bash
docker-compose logs -f
```

## 🌐 Acessar o WordPress

Após iniciar os containers, acesse:
- **WordPress**: http://localhost:8080

## 🔐 Credenciais do Banco de Dados

- **Host**: db
- **Database**: wordpress
- **User**: wordpress
- **Password**: wordpress_password
- **Root Password**: root_password


## 📦 Volumes

Os dados são persistidos nos seguintes volumes:
- `db_data`: Dados do MySQL
- `wordpress_data`: Arquivos do WordPress

## 🛠️ Comandos úteis

### Remover tudo (incluindo volumes):
```bash
docker-compose down -v
```

### Reconstruir os containers:
```bash
docker-compose up -d --build
```

### Acessar o container do WordPress:
```bash
docker exec -it wordpress_site bash
```

### Acessar o container do MySQL:
```bash
docker exec -it wordpress_db mysql -u root -p
```


### pos docker
```bash
    segue o passo a passo
    instala o All-in-one wp migration
    vai na extensao do lado esquerdo, importar e importa o inovare
    pronto, tem os dados rodando
    ```