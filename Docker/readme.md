
## PRÁCTICAS DOCKER.

## Práctica 2.

1.
![imagen](https://user-images.githubusercontent.com/72253934/223849404-aa726491-9d53-4953-afa1-3a90a0e0de96.png)


2. 

![imagen](https://user-images.githubusercontent.com/72253934/223849464-31f24af6-ed76-4384-b7a6-492237fc6414.png)

3.

![imagen](https://user-images.githubusercontent.com/72253934/223849529-faabf4d4-12f5-4e85-81a2-f41d92d5ac30.png) <br>
![imagen](https://user-images.githubusercontent.com/72253934/223849564-2530d7d8-b650-40d7-a0ee-9c1888a9aea0.png) <br> 
![imagen](https://user-images.githubusercontent.com/72253934/223849609-d5d3a6bc-d841-4dff-b447-a864a7c2327f.png) <br>
![imagen](https://user-images.githubusercontent.com/72253934/223850001-3a9ef3d2-b389-4e70-bba4-029535fab758.png) <br>
![imagen](https://user-images.githubusercontent.com/72253934/223850065-d9fdfd85-3f4b-43b1-bd99-c8039d163d00.png) <br>
![imagen](https://user-images.githubusercontent.com/72253934/223850223-be04d8d7-2f84-49ec-8985-de1674882bba.png) <br>
![imagen](https://user-images.githubusercontent.com/72253934/223850269-74cc7930-5946-4864-a3b0-953164ead458.png)

## Práctica 3. <br>
1.
![imagen](https://user-images.githubusercontent.com/72253934/223850746-8ac9d248-4d82-43c8-b124-70e62799ab61.png) <br>

2.

![imagen](https://user-images.githubusercontent.com/72253934/223850892-d552529c-0958-491a-91df-7b0fcfe7cffb.png) <br>

3.
![imagen](https://user-images.githubusercontent.com/72253934/223850983-b24f89ee-fecb-405f-9a89-06734a8efd68.png) <br>

4.
![imagen](https://user-images.githubusercontent.com/72253934/223851152-f716c533-73f3-47fa-94c4-e2c3d4d3bf2d.png) <br>

5.
![imagen](https://user-images.githubusercontent.com/72253934/223851206-60757ac0-b6f5-4dbf-a773-ebf5848b3d34.png) <br>

6.
![imagen](https://user-images.githubusercontent.com/72253934/223851274-f191ec83-13c2-4390-9f81-4e56c2e671a1.png) <br>

7.
![imagen](https://user-images.githubusercontent.com/72253934/223851340-b881e191-dc01-4f63-8447-021ec41f603a.png) <br>

8.
![imagen](https://user-images.githubusercontent.com/72253934/223851443-1744ed50-4bad-4e73-be8c-750e51e90fd9.png) <br>

9 y 10. <br>
![imagen](https://user-images.githubusercontent.com/72253934/223851515-3e935393-afdd-4685-beba-95f0fe097306.png) <br>

11.
![imagen](https://user-images.githubusercontent.com/72253934/223851547-77f22ce9-875d-4100-8bf6-f64ba8e0e14d.png) <br>

12.

![imagen](https://user-images.githubusercontent.com/72253934/223851812-7b927445-1ab2-4a23-81cc-9de52cef1e54.png) <br>

## PRACTICA 4

Creamos la red:  <br>
![imagen](https://user-images.githubusercontent.com/72253934/223852918-0e7613a3-6692-4738-9f61-5433a7890a9a.png) <br>

Y ponemos a funcionar el contenedor: <br>

![imagen](https://user-images.githubusercontent.com/72253934/223853013-448fb028-4597-4e3b-b92a-d9fdb28c1dda.png) <br>

![imagen](https://user-images.githubusercontent.com/72253934/223853073-ea63c02d-4617-4cd8-90e3-1817242a30cf.png) <br>

Segundo ejercicio: <br>

Basicamente haremos lo mismo pero con otra aplicación, por lo tanto dejaré las capturas con los comandos <br>

![imagen](https://user-images.githubusercontent.com/72253934/223853345-72312afb-c2e9-4c7d-8f22-0833c41e3903.png) <br>
![imagen](https://user-images.githubusercontent.com/72253934/223853412-597f0012-d83b-4882-beae-d12ab84a33df.png) <br>
![imagen](https://user-images.githubusercontent.com/72253934/223853550-9fe90909-a172-4b4f-aabf-25742be134de.png) <br>

Tercer ejercicio: <br> 

![imagen](https://user-images.githubusercontent.com/72253934/223853898-f60610c0-6141-4f70-88fb-e6dc43ef8356.png) <br>
![imagen](https://user-images.githubusercontent.com/72253934/223853955-5038402f-3f96-4102-8d38-b9173109d842.png)


—---------------------------------------------------------------------------------------------------------------------------------
<br>

## Práctica 5

Destacar en esta práctica que trabajaremos siempre con el fichero que nos proporciona la guía, en este primer ejemplo será el fichero Dockerfile con el siguiente contenido: <br> 

```yaml
version: '3.1'
services:
  app:
    container_name: guestbook
    image: iesgn/guestbook
    restart: always
    ports:
      - 80:5000
  db:
    container_name: redis
    image: redis
    restart: always
```
![imagen](https://user-images.githubusercontent.com/72253934/223855027-34922953-4397-4510-bb4c-7f892a4ff981.png)

—---------------------------------------------------------------------------------------------------------------------------------<br>
En este utilizaremos el siguiente fichero yml: <br>
```yaml
version: '3.1'
services:
  frontend:
    container_name: temperaturas-frontend
    image: iesgn/temperaturas_frontend
    restart: always
    ports:
      - 80:3000
    depends_on:
      - backend
  backend:
    container_name: temperaturas-backend
    image: iesgn/temperaturas_backend
    restart: always
```
![imagen](https://user-images.githubusercontent.com/72253934/223855124-e1e7d16b-cf52-4059-8c6b-7b08ab96e03d.png)

—---------------------------------------------------------------------------------------------------------------------------------<br>

```yaml
version: '3.1'
services:
  wordpress:
    container_name: servidor_wp
    image: wordpress
    restart: always
    environment:
      WORDPRESS_DB_HOST: db
      WORDPRESS_DB_USER: user_wp
      WORDPRESS_DB_PASSWORD: asdasd
      WORDPRESS_DB_NAME: bd_wp
    ports:
      - 80:80
    volumes:
      - wordpress_data:/var/www/html/wp-content
  db:
    container_name: servidor_mysql
    image: mariadb
    restart: always
    environment:
      MYSQL_DATABASE: bd_wp
      MYSQL_USER: user_wp
      MYSQL_PASSWORD: asdasd
      MYSQL_ROOT_PASSWORD: asdasd
    volumes:
      - mariadb_data:/var/lib/mysql
volumes:
    wordpress_data:
    mariadb_data:
```
![imagen](https://user-images.githubusercontent.com/72253934/223855274-dbbccec2-b626-48ed-acf1-8e40b6f3dcd9.png)


## Practica 6

Construcción de imágenes con una página estática. <br> 

Versión 1: <br>
Trabajaremos apartir del fichero proporcionado de la guía que aparece en el enunciado: <br>
```Dockerfile
FROM debian
RUN apt-get update && apt-get install -y apache2 && apt-get clean && rm -rf /var/lib/apt/lists/*
ADD public_html /var/www/html/
EXPOSE 80
CMD ["/usr/sbin/apache2ctl", "-D", "FOREGROUND"]
```

![imagen](https://user-images.githubusercontent.com/72253934/223855751-559f5b44-9dcb-40f2-91cf-bdb70f9bdd93.png) <br>
![imagen](https://user-images.githubusercontent.com/72253934/223855802-c3d1eac6-4f3d-4da3-90bd-c562c7ba80dc.png) <br>
![imagen](https://user-images.githubusercontent.com/72253934/223855841-9ee4bb5d-597f-46f0-a6e9-8051501785b7.png) <br>
![imagen](https://user-images.githubusercontent.com/72253934/223855869-272aa5c9-2348-47c3-a66d-f04874926158.png) <br>

Versión 2: <br>

```Dockerfile
FROM httpd:2.4
ADD public_html /usr/local/apache2/htdocs/
EXPOSE 80
```
![imagen](https://user-images.githubusercontent.com/72253934/223856454-e86c486f-1e4a-4296-964e-8b45091b1745.png) <br>
![imagen](https://user-images.githubusercontent.com/72253934/223856498-c0ef579f-89f3-4d9b-93ab-e77e9d3b8cce.png) <br>
![imagen](https://user-images.githubusercontent.com/72253934/223892120-6f0133de-a31d-437e-838a-0081a3ad5b94.png)


Versión 3:  <br>
```Dockerfile
FROM nginx
ADD public_html /usr/share/nginx/html
EXPOSE 80
```
![imagen](https://user-images.githubusercontent.com/72253934/223856574-d23e9f71-a82e-45b8-9819-b64c88bd3b49.png) <br>


parte 2:







version 2:

----------------------------------------------------------------------------------------------------------------------------------<br>

Construcción de imágenes con una una aplicación Python: <br>
```Dockerfile
FROM debian
RUN apt-get update && apt-get install -y python3-pip  && apt-get clean && rm -rf /var/lib/apt/lists/*
COPY app /usr/share/app
WORKDIR /usr/share/app
RUN pip3 install --no-cache-dir -r requirements.txt
EXPOSE 3000
CMD [ "python3", "app.py"]
```
![imagen](https://user-images.githubusercontent.com/72253934/223857695-70aee21f-2b3d-4b0d-8f89-272db05e0417.png) <br>
![imagen](https://user-images.githubusercontent.com/72253934/223890473-64b586e1-bbda-420c-85ed-a4db78cbc16a.png) <br>
![imagen](https://user-images.githubusercontent.com/72253934/223890698-aec18323-72de-46c6-b1fd-a4cd8d41c9cf.png) <br>

