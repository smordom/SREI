 ## Recuperación de Docker 1º Trimestre 

Instalación del servidor web apache mediante docker.

Actualizamos los repositorios con:
- "sudo apt update" <br>
![imagen](https://github.com/smordom/SREI/assets/72253934/c535e124-bcbd-4514-9f23-be9738aaccb3)

Luego realizamos un: 
- docker run -dit --name apachesamu -p 8080:80 httpd:2.4 <br>
 
 ![imagen](https://github.com/smordom/SREI/assets/72253934/fd7e16a5-2f1b-4ffe-8ba8-4b32e414e16b)

Y comprobamos que esté funcionando por el puerto 8080: <br>
![imagen](https://github.com/smordom/SREI/assets/72253934/8022b27d-6e73-4906-8029-4f5ba14c7dcb)
