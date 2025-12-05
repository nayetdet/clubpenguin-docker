# Club Penguin Docker (Yukon)
Este projeto é uma implementação **dockerizada do Yukon** para criar e rodar servidores privados de **Club Penguin** de forma simples e isolada usando **Docker** e **Docker Compose**.

## Pré-requisitos

- `git`
- `Docker`
- `Docker Compose`

## Como iniciar o servidor

1. **Clonar o repositório**

   ```bash
   git clone --recurse-submodules https://github.com/nayetdet/clubpenguin-docker
   cd clubpenguin-docker
   ```

2. **Criar o arquivo de ambiente**

   Crie um arquivo chamado `.env` na raiz do projeto, com as variáveis necessárias para o seu servidor Yukon / Club Penguin (por exemplo, portas, credenciais, URLs etc.).

   Exemplo (apenas ilustrativo, ajuste conforme sua necessidade):

   ```env
   MYSQL_ROOT_PASSWORD="root"
   MYSQL_USER="user"
   MYSQL_PASSWORD="user123"
   MYSQL_DATABASE="yukon"
   ```

3. **Subir os containers com Docker Compose**

   Use o comando abaixo para iniciar todos os serviços em segundo plano, utilizando o arquivo `.env` que você criou:

   ```bash
   docker compose --env-file .env up -d
   ```

4. **Verificar se está rodando**

   ```bash
   docker compose ps
   ```

   Se tudo deu certo, você verá os containers do Yukon/Club Penguin em execução.

## Parar e remover os containers

Para parar os serviços:

```bash
docker compose down
```

Se quiser parar e também remover volumes/recursos associados, use:

```bash
docker compose down -v
```

---

Se quiser, posso te ajudar a definir um exemplo real de `.env` baseado na configuração específica do seu servidor Yukon.
