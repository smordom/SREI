# Práctica Servidores WEB      2º Trimestre

1. Se dará alojamiento a páginas web tanto estáticas como dinámicas con “php”. <br>
Actualizamos nuestros repositorios con "sudo apt update",
![imagen](https://user-images.githubusercontent.com/72253934/221395514-9f0825ff-1b33-44cd-925d-03eee69d5953.png) <br>
E instalamos php con "sudo apt install apache2"
![imagen](https://user-images.githubusercontent.com/72253934/221395568-c76516ca-7d61-41d8-a47f-f50f2e953528.png) <br>

Y por último ajustaremos el firewall para permitir el tráfico web y permitiremos a Apache: 

- sudo ufw app list <br>
- sudo ufw app info “Apache Full” <br>
- sudo ufw allow “Apache Full” <br>

![imagen](https://user-images.githubusercontent.com/72253934/221395843-5037768a-79c8-49aa-b2a2-281d6eb1f261.png)

Reiniciamos apache server con: sudo systemctl restart apache2 <br>
Y comprobaremos  su estado con: sudo systemctl status apache2 <br>

![imagen](https://user-images.githubusercontent.com/72253934/221395943-c06e684a-bf42-4731-9c52-a9ed594ebb18.png) <br>

Ahora instalaremos PHP: <br>
![imagen](https://user-images.githubusercontent.com/72253934/221396028-e98ec48b-af6c-413f-a6ec-b5fa6b7ed89f.png) <br>

2. Los clientes dispondrán de un directorio de usuario con una página web
por defecto. <br>

En la carpeta HTML crearemos una carpeta de usuario con un index.html para que tenga una página web diferente a la de por defecto. <br>
Al haber instalado php tambien podríamos añadir una página dinámica.
![imagen](https://user-images.githubusercontent.com/72253934/221397684-a418f428-81c0-4356-959b-03a493f7d51c.png) <br>
![imagen](https://user-images.githubusercontent.com/72253934/221397697-5155bbcd-6d20-484c-9900-d7532b2b5033.png) <br>
![imagen](https://user-images.githubusercontent.com/72253934/221397731-960068db-bd11-4ed2-a2df-ef2cf463cbac.png)

3. Además contarán con una base de datos sql que podrán administrar con phpmyadmin. <br>

Instalamos MySQL con:
- sudo apt install mysql-server

![imagen](https://user-images.githubusercontent.com/72253934/221398124-5d9b857f-9eb0-43fe-8f8e-e32430127f6f.png)
<br>
Instalamos phpMyAdmin con: 
- sudo apt install phpmyadmin <br>

![imagen](https://user-images.githubusercontent.com/72253934/221398170-b29379f5-8857-44c5-b2ec-8e7bb7725246.png)

Seleccionamos sí: 

![imagen](https://user-images.githubusercontent.com/72253934/221398224-7ae03e24-6ca8-4082-88c5-9229c5000d06.png) <br>

Y ponemos una contraseña: 
![imagen](https://user-images.githubusercontent.com/72253934/221398258-c82b4062-3022-41b7-819e-2591ab41259f.png) <br>

Al buscar localhost/phpmyadmin/ en el navegador, no mostraba la página principal de php por lo cual también hemos <br>
lo siguiente: <br>
- sudo -H gedit /etc/apache2/apache2.conf
![imagen](https://user-images.githubusercontent.com/72253934/221398663-801ea4d8-cb3f-4785-a7be-0875b241f534.png) <br>

Añadimos al final del archivo:
Include /etc/phpmyadmin/apache.conf <br>
![imagen](https://user-images.githubusercontent.com/72253934/221398693-b6ac9912-d495-42a3-a976-c26c50b24166.png) <br>

Y reiniciamos apache:
- /etc/init.d/apache2 restart <br>

Y ya estaría funcionando la página principal de Apache: 
![imagen](https://user-images.githubusercontent.com/72253934/221398770-cfac64a7-8bd7-4d02-93fb-043a75edcaaa.png) <br> <br>

4. Los clientes podrán acceder mediante ftp para la administración de
archivos configurando adecuadamente TLS.

Instalamos ftp con el mando sudo apt-get install proftpd <br>

Una vez instalado tenemos que editar su archivo de configuración, donde configuraremos el nombre del servidor, usuarios: <br>

![imagen](https://user-images.githubusercontent.com/72253934/221399293-092c74a0-ab52-47ce-8996-a804017d82fe.png) <br>
![imagen](https://user-images.githubusercontent.com/72253934/221399339-12b9f5b5-1d16-418e-a831-2515ea36b389.png) <br>
![imagen](https://user-images.githubusercontent.com/72253934/221399405-d9069deb-8fe0-4732-a6ac-cb10a8a2db0d.png) <br>
![imagen](https://user-images.githubusercontent.com/72253934/221399430-a9e7baf9-1ffe-459f-ac9f-e41eacf64709.png)
<br> <br> 

Escribimos el siguiente comando para comprobar si hay errores de sintaxis:
- sudo proftpd -t <br>
![imagen](https://user-images.githubusercontent.com/72253934/221399872-f2a91501-5156-4512-970e-469c92a50e3e.png)

## DNS
