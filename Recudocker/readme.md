 ## Recuperación de Docker 1º Trimestre 

#### 1.Instalación del servidor web apache mediante docker.

Actualizamos los repositorios con:
- "sudo apt update" <br>
![imagen](https://github.com/smordom/SREI/assets/72253934/c535e124-bcbd-4514-9f23-be9738aaccb3)

Luego realizamos un: 
- docker run -dit --name apachesamu -p 8080:80 httpd:2.4 <br> 
 ![imagen](https://github.com/smordom/SREI/assets/72253934/fd7e16a5-2f1b-4ffe-8ba8-4b32e414e16b)

Y comprobamos que esté funcionando por el puerto 8080: <br>
![imagen](https://github.com/smordom/SREI/assets/72253934/8022b27d-6e73-4906-8029-4f5ba14c7dcb)

#### 2. Instalación MYSQL

En primer lugar lo que haremos será descargar la imagen mediante:
- docker pull mysql <br> <br>
![imagen](https://github.com/smordom/SREI/assets/72253934/4a39ca61-cfb7-447d-b5c3-a0c63ba404ae) <br> <br>

Una vez hecho esto podremos iniciaremos el contenedor y comprobamos que está funcionando correctamente: <br> <br>
![imagen](https://github.com/smordom/SREI/assets/72253934/a5322516-1144-4541-8e19-8ec4c5628484)

Aquí realizaremos un docker exec para acceder a nuestro contenedor y usar mysql: <br> <br>
![imagen](https://github.com/smordom/SREI/assets/72253934/eff88581-11f9-4eba-89d2-12053690c3f0)

Ahora configuraremos MySQL y crearemos un usuario y le daremos permisos: <br> <br>
![imagen](https://github.com/smordom/SREI/assets/72253934/133b22c4-7dee-4ea6-b21b-0e6f91128b64) <br>
![imagen](https://github.com/smordom/SREI/assets/72253934/caa9e449-d3fa-465f-8186-adb2ae5b1ea8) <br>

#### 3. Instalacion Wordpress

Para instalar Wordpress lo primero que haremos será crear la siguiente estructura y un archivo yml: <br>
![imagen](https://github.com/smordom/SREI/assets/72253934/2c7fca5e-ca2d-488e-b02e-af324ff990d3) <br>

El archivo yml contendrá la siguiente información: 

```version: '3'
services:
  db:
    image: mysql:5.7
    volumes:
      - db_data:/var/lib/mysql
    restart: always
    environment:
      MYSQL_ROOT_PASSWORD: 1234
      MYSQL_DATABASE: wordpress
      MYSQL_USER: wordpress
      MYSQL_PASSWORD: 1234

  wordpress:
    depends_on:
      - db
    image: wordpress:latest
    ports:
      - "8000:80"
    restart: always
    environment:
      WORDPRESS_DB_HOST: db:3306
      WORDPRESS_DB_USER: wordpress
      WORDPRESS_DB_PASSWORD: 1234
      WORDPRESS_DB_NAME: wordpress
volumes:
  db_data:
```
Una vez hecho esto hacemos un:
- docker-compose up -d
<br>

![imagen](https://github.com/smordom/SREI/assets/72253934/62fd8787-a83f-48d5-ba30-af2f6fc55647) <br> 

Y así nuestro contenedor con Wordpress estaría funcionando de manera correcta.

