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

#### 4. Configuración AWSTATS

En primer lugar crearemos una carpeta para awstats, y crearemos un docker-compose con la siguiente información:

```
version: '3'
services:
  awstats:
    image: justb4/awstats:latest
    volumes:
      - ./data:/etc/awstats
    ports:
      - "8080:80"
```
![imagen](https://github-production-user-asset-6210df.s3.amazonaws.com/72253934/241195162-3088af11-f171-431c-a4d6-532c513185b6.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAIWNJYAX4CSVEH53A%2F20230526%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20230526T111743Z&X-Amz-Expires=300&X-Amz-Signature=b2454119e3204c4e9548ec265d13c11ff9e334799e350125f11acca6f0519f5f&X-Amz-SignedHeaders=host&actor_id=72253934&key_id=0&repo_id=542439151)

Lo siguiente que haremos será montar nuestro contenedor con:

- docker-compose up-d <br> 
![imagen](https://github.com/smordom/SREI/assets/72253934/eaf379b7-61aa-4cf3-9362-b80a30e32831)

<br>

Y accederemos a localhost para comprobar que funciona: <br>

![imagen](https://github.com/smordom/SREI/assets/72253934/0e4102d5-34c5-420d-a92a-f8bb0664400b)

Ahora mismo no nos está mostrando datos porque AWSTATS necesita tener una carpeta data en el lugar donde se ha montado el contenedor y añadirle la información a mostrar.

#### 5. Servidor NGINX con PHP.

Para crear nuestro servidor NGINX con PhP, lo primero que haremos será crear una carpeta de trabajo. Dentro crearemos un archivo yml con el nombre docker-compose.yml y añadiremos la siguiente información en él: <br> 

![imagen](https://github.com/smordom/SREI/assets/72253934/129a4460-b0ff-4ee3-b669-7ac23467002b) <br> <br> 

Una vez hecho esto también crearemos un archivo llamado "defaul.conf" al cual añadiremos la siguiente información: <br> <br> 
![imagen](https://github.com/smordom/SREI/assets/72253934/23d45c26-679f-400d-aa12-a5d1ae78d9ff) <br>
Así pues levantaremos nuestro contenedor una vez más con:
- docker-compose up -d <br>

Esto generará una carpeta nombrada "src", aquí dentro haremos un archivo index.php con el siguiente contenido:

```
<?php
  echo phpinfo();
  
```
Y finalmente accederemos a nuestro localhost para comprobar que nos muestra la información:
![imagen](https://github.com/smordom/SREI/assets/72253934/2638cd6d-bf39-47b0-a6fe-2a733190df00)
