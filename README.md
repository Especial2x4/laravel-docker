# Manual de instrucciones

En la raíz del proyecto crear los volúmenes que hacen falta

```
mkdir dbdata src
```

## Levantar el contenedor

``` 
docker compose up -d --build 
```

## Configurar MySQL

```
docker exec -it laravel_app bash
```
```
vim /var/www/.env
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

Guardar el archivo

```
php artisan migrate
```
```
php artisan tinker
```
```
DB::connection()->getPdo();
```

Si no aparece ningún error parar el contenedor y volver a ejecutarlo

```
docker compose down
docker compose up -d --build
```
## Probar en el navegador

Ingresar al navegador haciendo uso del puerto 8080






