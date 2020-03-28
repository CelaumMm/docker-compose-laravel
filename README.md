# docker-compose-laravel

Um ambiente de desenvolvimento simplificado em docker, com uma rede LEMP de containers para o desenvolvimento local de um aplicativo em  Laravel.

## Requisitos

-   [Git](https://git-scm.com/)
-   [Docker](https://docs.docker.com/docker-for-windows/install/)


## Instalação

1. Efetuar a instalação clonando ou baixando do repositorio.

    ```bash
    git clone https://github.com/CelaumMm/docker-compose-laravel.git
    ```

    ```bash
    git clone git@github.com:CelaumMm/docker-compose-laravel.git
    ```

    OU Dowload [docker-compose-laravel](https://github.com/CelaumMm/docker-compose-laravel/archive/master.zip)


2. Entrar na pasta do projeto, execute:
    
    ```bash
    cd docker-compose-laravel
    ```

3. Instalar o projeto laravel na pasta `src`

    ```bash
    cd src
    composer create-project --prefer-dist laravel/laravel .
    ````

4. Construindo os containers

    Execute o comando na raiz do projeto, onde fica o arquivo docker-compose.yml
    ```bash
    docker-compose up -d --build
    ```

5. Abra o navegador de sua escolha [http://localhost:8080](http://localhost:8080)

6. O aplicativo Laravel precisa estar no diretório src primeiro antes de abrir os containers, caso contrário, o container artisan não vai funcionar.

7. Configurar no arquivo .env o acesso ao MySql

    ```bash
    DB_HOST=mysql
    DB_DATABASE=laravel
    DB_USERNAME=laravel
    DB_PASSWORD=secret
    ```

8. Criar as tabelas com o migrate

    ```bash
    docker-compose run --rm artisan migrate
    ```

9. Foi adicionado containers que manipulam os comandos do Composer, NPM e Artisan. Use os seguintes comandos na raiz do projeto, modificando-os ao seu caso de uso específico:

    ```bash
    docker-compose run --rm composer install
    docker-compose run --rm composer update
    docker-compose run --rm composer require ...
    docker-compose run --rm npm install
    docker-compose run --rm npm run dev
    docker-compose run --rm artisan migrate
    ```

8. Os Containers criados e suas portas são as seguintes:

    - **nginx** - `:8080`
    - **mysql** - `:3306`
    - **php** - `:9000`
    - **npm**
    - **composer**
    - **artisan**


9. Outros comandos docker

    Iniciar os containers
    ```bash
    docker-compose up -d
    ```

    Destruir os containers
    ```bash
    docker-compose down
    ```

    Parar os containers
    ```bash
    docker-compose stop
    ```

    Reiniciar todos os containers
    ```bash
    docker-compose restart
    ```

    Reiniciar um container especifico
    ```bash
    docker-compose restart nginx
    ```