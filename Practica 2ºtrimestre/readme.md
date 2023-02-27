# Práctica Servidores WEB      2º Trimestre

## 1. Se dará alojamiento a páginas web tanto estáticas como dinámicas con “php”. <br>
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

## 2. Los clientes dispondrán de un directorio de usuario con una página web
por defecto. <br>

En la carpeta HTML crearemos una carpeta de usuario con un index.html para que tenga una página web diferente a la de por defecto. <br>
Al haber instalado php tambien podríamos añadir una página dinámica.
![imagen](https://user-images.githubusercontent.com/72253934/221397684-a418f428-81c0-4356-959b-03a493f7d51c.png) <br>
![imagen](https://user-images.githubusercontent.com/72253934/221397697-5155bbcd-6d20-484c-9900-d7532b2b5033.png) <br>
![imagen](https://user-images.githubusercontent.com/72253934/221397731-960068db-bd11-4ed2-a2df-ef2cf463cbac.png)

## 3. Además contarán con una base de datos sql que podrán administrar con phpmyadmin. <br>

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

## 4. Los clientes podrán acceder mediante ftp para la administración de
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

El primer paso es instalar bind con los comandos: <br>
- sudo apt-get update
- sudo apt-get install bind9 bind9utils bind9-doc
<br>

Editamos el primer archivo de configuración con: <br>

-sudo nano /etc/bind/named.conf.options <br>

![imagen](https://user-images.githubusercontent.com/72253934/221602148-ab43b3e4-9408-439d-a1e9-0e8365f48ddc.png)
<br>

Editamos el otro archivo de configuración: <br>
- sudo nano /etc/bind/named.conf.local 
<br>

![imagen](https://user-images.githubusercontent.com/72253934/221599908-8f9a7dcd-1fb0-470b-a64b-81f99e92b83d.png)

<br>

Fichero hosts: 
![imagen](https://user-images.githubusercontent.com/72253934/221599339-89cf0597-6803-4f8c-b142-fd0f6bf583be.png) 
<br>

Comprobamos que el DNS contesta con: <br>

- dig google.com

![imagen](https://user-images.githubusercontent.com/72253934/221611456-daf9b553-8a08-44d5-87b1-8fec27d18821.png)
<br>

Y con esto ya habríamos configurado el DNS. <br>

Ahora bien, para acceder mediante TLS, debemos instalar OpenSSL con el comando: <br>

- apt-get install proftpd openssl <br>
![imagen](https://user-images.githubusercontent.com/72253934/221611999-c60b8359-6e7f-4a7c-aa45-122b3b119cfb.png)
<br>

Una vez instalado creamos un directorio donde guardar nuestros certificados llamado ssl con: <br>
- sudo mkdir /etc/proftpd/ssl
<br>

Introducimos el siguiente comando para generar los certificados: 
- sudo openssl req -new -x509 -days 365 -nodes -out /etc/proftpd/ssl/proftpd.cert.pem -keyout /etc/proftpd/ssl/proftpd.key.pem

![imagen](https://user-images.githubusercontent.com/72253934/221613879-333fe879-a06e-422a-9d0e-44881831864c.png)
<br> 

Le daremos permisos de escritura/lectura al usuario propietario únicamente:

- sudo chmod 600 /etc/proftpd/ssl/proftpd.*

![imagen](https://user-images.githubusercontent.com/72253934/221614778-5e18ecd7-25f6-4d21-84d5-51fa2642549b.png)
<br>

Para habilitar TLS en ProFTPd nos vamos a :
- nano /etc/proftpd/proftpd.conf <br>
y debajo de la línea comentada #This is used for FTPS Connections descomentamos: <br>

- Include /etc/proftpd/tls.conf

Ahora abrimos el archivo de configuración de TLS con sudo nano
/etc/proftpd/tls.conf descomentamos las rutas del certificado y modificamos
opciones.

![imagen](https://user-images.githubusercontent.com/72253934/221621067-463cc2c0-12e4-40c4-a975-30f9951d121d.png)
<br> 

![imagen](https://user-images.githubusercontent.com/72253934/221621238-8593a376-f1d0-4f1b-a487-d8067171971f.png) <br>

Y reiniciamos el servicio como hemos hecho anteriormente con: <br>

- Systemctl restart proftpd.service
- Systemctl status proftpd.service
<br> 

![imagen](https://user-images.githubusercontent.com/72253934/221625601-88d666bf-c017-47f4-8a10-df577431000c.png) <br>

Una vez hecho esto desde filezilla con la ip, el usuario y contraseña podremos acceder a los archivos del sistema.<br>

![imagen](https://user-images.githubusercontent.com/72253934/221648534-ce87cb8f-a0f0-4e8f-ad11-55325dcec871.png)

 ## 5. Se habilitará el acceso mediante ssh y sftp. <br>
 
El primer paso es instalar el paquete openssh con el comando: <br>

- sudo apt-get install openssh-server openssh-server

![imagen](https://user-images.githubusercontent.com/72253934/221649355-45bcb04e-4b49-4f9e-a54e-d148213c35ec.png) <br>

Una vez instalado editamos el archivo de configuración en sudo nano /etc/ssh/sshd_config, modificamos el puerto para evitar accesos indebidos, añadimos el usuario que queremos que tenga permisos y si queremos evitamos acceso al root por ssh. <br>

![imagen](https://user-images.githubusercontent.com/72253934/221651206-1910b9cc-5496-443d-9015-bfe40e46fa2d.png) <br>
![imagen](https://user-images.githubusercontent.com/72253934/221651340-2760fc93-a0e2-4977-8e5b-e145fea6c473.png) <br>
![imagen](https://user-images.githubusercontent.com/72253934/221651454-1845ff6d-fd9c-40bd-8a5b-995d24a1d528.png) <br>

Escribimos sudo service ssh restart para reiniciar el servicio. <br>

Una vez hecho esto podemos acceder desde otro equipo en la misma red con el comando ssh -p (puerto) (usuario)@(ip de la maquina a la que nos queremos
conectar)

![imagen](https://user-images.githubusercontent.com/72253934/221653167-f9f30d0d-71ab-415c-ac2f-08866342afe1.png) <br>

También se puede acceder desde sftp, como hemos personalizado el puerto en vez de utilizar el por defecto tenemos que escribir sftp -oPort=(puerto)(usuario)@(ip de la maquina a la que nos queremos conectar)

![imagen](https://user-images.githubusercontent.com/72253934/221657574-5e567479-cac3-42af-9f9d-04135eadd1e2.png) <br>

## 6. Se configura de forma adecuada postfix y dovecot imap y pop3

El primer paso es la instalación de postfix, thunderbird con imapd y pop3d. 

- sudo apt install postfix dovecot-imapd dovecot-pop3d mailutils thunderbird

![imagen](https://user-images.githubusercontent.com/72253934/221657963-9f62f990-b0e1-4c9e-90a8-5d7981cd2784.png) <br>

Una vez instalado posfix editamos main.cf , añadimos en mydestination marisma.local.

![imagen](https://user-images.githubusercontent.com/72253934/221659961-4a990fbe-6ef8-4b35-877d-04115d073436.png) <br>

Y ahora creamos un usuario con adduser, al que mandarle correos.

![imagen](https://user-images.githubusercontent.com/72253934/221660528-d8c31c6c-8ddc-49c8-bac2-077d3f128cf2.png) <br>

Para enviar correos desde un usuario escribimos: 
- echo “contenido” | mail -s “asunto” samu@marisma.local

Los correos del servidor siempre van con nombre de dominio <br>

Ahora nos loggeamos con el usuario al que le hemos enviado el correo y con el comando mail podemos comprobar que lo ha recibido.
                                                                
![imagen](https://user-images.githubusercontent.com/72253934/221663378-657c3e07-3783-4661-87f1-d78e9227ebdb.png) <br>

Para configurar thunderbird entramos en la aplicación y añadimos el usuario con su respectivo correo de dominio

![imagen](https://user-images.githubusercontent.com/72253934/221663744-0e38877d-2a79-4a45-90d4-7115886d3d11.png) <br>

En la configuración manual podemos seleccionar el tipo de seguridad y los puertos de los diferentes protocolos, tenemos instalados los protocolos IMAP y POP3, el protocolo IMAP trabaja por defecto con el puerto 143 y el POP3 con el puerto 110.

![imagen](https://user-images.githubusercontent.com/72253934/221664336-0e027ef0-85fc-44ce-bae1-841d54783207.png) <br>

Hemos utilizado solo POP3, sin embargo podemos añadir en Configuración de las cuentas otro protocolo al mismo correo: <br>

![imagen](https://user-images.githubusercontent.com/72253934/221665052-d33f660e-d162-45a2-8f12-5bc40d10d151.png) <br>

7. Se automatizará mediante el uso de scripts:
- La creación de usuarios y del directorio correspondiente para el alojamiento web
- Host virtual en apache
- Creación de usuario del sistema para acceso a ftp, ssh, smtp, ...
- Se creará un subdominio en el servidor DNS con las resolución directa e inversa <br>

El primer Script que realizaremos erá para la creación de nuevos usuarios, encargado de pedir nombre/contraseña y acto seguido creará una carpeta con el nombre del usuario en la carpeta HTML de var. <br>

![imagen](https://user-images.githubusercontent.com/72253934/221667326-0656446a-b41d-49dd-81d5-fa5366879248.png) <br>
