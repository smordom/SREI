
 ## Prácticas docker.

Práctica 2.

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

#### Práctica 3. <br>
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

#### PRACTICA 4

Utilizaremos el siguient archivo yml en nuestro directorio: <br>

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


—---------------------------------------------------------------------------------------------------------------------

Práctica 5
Utilizando el fichero que nos proporciona hacemos esto 



—---------------------------------------------------------------------------------------------------------------------



—---------------------------------------------------------------------------------------------------------------------




Practica 6



version 2

FROM httpd:2.4
ADD public_html /usr/local/apache2/htdocs/
EXPOSE 80





Version 3: 



parte 2:







version 2:






