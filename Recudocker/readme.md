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
![imagen](https://github.com/smordom/SREI/assets/72253934/4a39ca61-cfb7-447d-b5c3-a0c63ba404ae) <br>

Una vez hecho esto podremos iniciaremos el contenedor y comprobamos que está funcionando correctamente: <br> <br>
![imagen](https://github.com/smordom/SREI/assets/72253934/a5322516-1144-4541-8e19-8ec4c5628484)

![imagen](https://github.com/smordom/SREI/assets/72253934/eff88581-11f9-4eba-89d2-12053690c3f0)
