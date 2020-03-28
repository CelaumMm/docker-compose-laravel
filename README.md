# docker-compose-laravel

Um ambiente de desenvolvimento simplificado em docker, com uma rede LEMP de containers para o desenvolvimento local do Laravel.

## Como usar

Verifique se o [Docker](https://docs.docker.com/docker-for-windows/install/) está instalado no seu sistema e depois clone este repositório.


## Instalar projeto laravel

Adicione todo o seu projeto Laravel à pasta `src` ou instale um projeto laravel do zero, execute:

```
cd src
composer create-project --prefer-dist laravel/laravel .
````

## Construindo os containers

Execute o comando na raiz do projeto, onde fica o arquivo docker-compose.yml
```
docker-compose up -d --build
```

Abra o navegador de sua escolha [http://localhost:8080](http://localhost:8080)

**OBS:** O aplicativo Laravel precisa estar no diretório src primeiro antes de abrir os containers, caso contrário, o container artisan não vai funcionar.

## Configurar o arquivo .env do laravel

```
DB_HOST=mysql
DB_DATABASE=laravel
DB_USERNAME=laravel
DB_PASSWORD=secret
```

## Criando as tabelas com o migrate

```
docker-compose run --rm artisan migrate
```


## Containers

Foi adicionado containers que manipulam os comandos do Composer, NPM e Artisan sem precisar dessas plataformas estar instaladas no computador local. Use os seguintes comandos na raiz do projeto, modificando-os para se ajustarem ao seu caso de uso específico:

- `docker-compose run --rm composer install`
- `docker-compose run --rm composer update`
- `docker-compose run --rm composer require ...`
- `docker-compose run --rm npm install`
- `docker-compose run --rm npm run dev`
- `docker-compose run --rm artisan migrate` 

Containers criados e suas portas são as seguintes:

- **nginx** - `:8080`
- **mysql** - `:3306`
- **php** - `:9000`
- **npm**
- **composer**
- **artisan**


## Outros comandos docker

Iniciar os containers
```
docker-compose up -d
```

Destruir os containers
```
docker-compose down
```

Parar os containers
```
docker-compose stop
```

Reiniciar todos os containers
```
docker-compose restart
```

Reiniciar um container especifico
```
docker-compose restart nginx
```