# Manual de instrucciones

En la raíz del proyecto crear los volúmenes que hacen falta

```
mkdir dbdata src
```

## Levantar el contenedor

``` 
docker compose up -d --build 

```

## Instalar Laravel

``` 
docker exec -it laravel_app bash

```

``` 
composer create-project --prefer-dist laravel/laravel .

```

``` 
chmod -R 775 storage
chmod -R 775 bootstrap/cache
chown -R www-data:www-data storage
chown -R www-data:www-data bootstrap/cache

```

``` 
docker-compose down
docker-compose up -d

```



## Configurar MySQL

Salir del contenedor e ir a la raíz del directorio src y editar el archivo .env

```
vim .env
```

Configurar estas líneas en el contenido del archivo .env

```
DB_CONNECTION=mysql
DB_HOST=laravel_db
DB_PORT=3306
DB_DATABASE=laravel
DB_USERNAME=laraveluser
DB_PASSWORD=password
```

Guardar el archivo y volver al contenedor

```
docker exec -it laravel_app php artisan migrate

```

Salir del contenedor y reiniciar

``` 
docker-compose down
docker-compose up -d

```

```
docker exec -it laravel_app bash

```

```
php artisan migrate
```
```
php artisan tinker
```
```
DB::connection()->getPdo();
```

Si no aparece ningún error, salir y parar el contenedor y volver a ejecutarlo

```
docker compose down
docker compose up -d --build
```
## Probar en el navegador

Ingresar al navegador haciendo uso del puerto 8080






