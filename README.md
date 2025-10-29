# WordPress com Docker

Este projeto contém a configuração Docker para rodar WordPress com MySQL e phpMyAdmin.

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

## 🌐 Acessar os serviços

Após iniciar os containers, acesse:
- **WordPress**: http://localhost:8080
- **phpMyAdmin**: http://localhost:8081
- **MySQL**: localhost:3306

## 🔐 Credenciais do Banco de Dados

- **Host**: db (ou localhost:3306 externamente)
- **Database**: wordpress
- **User**: wordpress
- **Password**: wordpress_password
- **Root Password**: root_password

⚠️ **IMPORTANTE**: Altere as senhas antes de usar em produção!

## 📦 Volumes

Os dados são persistidos nos seguintes volumes:
- `db_data`: Dados do MySQL
- `wordpress_data`: Arquivos do WordPress
- `./mysql-backup`: Pasta local para backups do banco

## ✨ Recursos adicionados

### 🎯 MySQL
- ✅ Charset UTF-8 (utf8mb4)
- ✅ Healthcheck automático
- ✅ Porta 3306 exposta para conexões externas
- ✅ Pasta de backup mapeada

### 🎨 WordPress
- ✅ Memory limit: 256MB
- ✅ Max memory limit: 512MB
- ✅ Upload de arquivos: até 64MB
- ✅ Debug mode ativado
- ✅ Tempo de execução estendido (300s)

### 🗄️ phpMyAdmin
- ✅ Interface web para gerenciar o banco
- ✅ Acesso em http://localhost:8081

## 🛠️ Comandos úteis

### Backup do banco de dados:
```bash
docker exec wordpress_db mysqldump -u root -proot_password wordpress > mysql-backup/backup-$(date +%Y%m%d-%H%M%S).sql
```

### Restaurar backup:
```bash
docker exec -i wordpress_db mysql -u root -proot_password wordpress < mysql-backup/backup.sql
```

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
docker exec -it wordpress_db mysql -u root -proot_password
```

### Ver logs de um serviço específico:
```bash
docker-compose logs -f wordpress
docker-compose logs -f db
docker-compose logs -f phpmyadmin
```

## 🔧 Configurações personalizadas

O arquivo `uploads.ini` contém configurações PHP personalizadas:
- Upload máximo: 64MB
- Memory limit: 256MB
- Tempo de execução: 300s
