# Práctica Servidores WEB      1º Trimestre

Instalación del servidor web apache Usaremos dos dominios mediante el archivo hosts: centro.intranet y departamentos.centro.intranet. El primero servirá el contenido mediante wordpress y el segundo una aplicación en python.

Actualizamos los repositorios con: “sudo apt update”

![imagen](https://github.com/smordom/SREI/blob/main/1%C2%BA%20Trimestre/Trabajo%201%C2%BA%20Trimestre/Capturas/sudo_apt_update.png)

Procedemos a instalar apache2 mediante el siguiente comando: 
- sudo apt install apache2

![imagen](https://github.com/smordom/SREI/blob/main/1%C2%BA%20Trimestre/Trabajo%201%C2%BA%20Trimestre/Capturas/sudo_apt_install_apache2.png)

Ajustaremos el firewall para permitir el tráfico web y permitiremos a Apache: 

- sudo ufw app list <br>
- sudo ufw app info “Apache Full” <br>
- sudo ufw allow “Apache Full” <br>

![imagen](https://github.com/smordom/SREI/blob/main/1%C2%BA%20Trimestre/Trabajo%201%C2%BA%20Trimestre/Capturas/ufw_app_list.png)

Y con esto ya tendríamos listo apache y funcionando: 

![imagen](https://github.com/smordom/SREI/blob/main/1%C2%BA%20Trimestre/Trabajo%201%C2%BA%20Trimestre/Capturas/apache_funcionando.png)

Reiniciamos apache server con: sudo systemctl restart apache2 <br>
Y comprobaremos  su estado con: sudo systemctl status apache2 

![imagen](https://github.com/smordom/SREI/blob/main/1%C2%BA%20Trimestre/Trabajo%201%C2%BA%20Trimestre/Capturas/reiniciar_sistema.png)

Añadir el dominio “centro.intranet” y “departamento.centro.intranet” en el fichero “host” con "nano /etc/hosts" y añadiremos lo siguiente: <br>

- 127.0.0.1 centro.intranet <br>
- 127.0.0.1 departamento.centro.intranet

![imagen](https://github.com/smordom/SREI/blob/main/1%C2%BA%20Trimestre/Trabajo%201%C2%BA%20Trimestre/Capturas/url_centrointranet.png)

Creamos un archivo de configuración para el dominio: <br>
- sudo nano /etc/apache2/sites-available/centro.intranet.conf

Después de añadir los datos de virtualhost habilitamos el site "sudo a2ensite centro.intranet"

![imagen](https://github.com/smordom/SREI/blob/main/1%C2%BA%20Trimestre/Trabajo%201%C2%BA%20Trimestre/Capturas/nano_centrointranet.png)

![imagen](https://github.com/smordom/SREI/blob/main/1%C2%BA%20Trimestre/Trabajo%201%C2%BA%20Trimestre/Capturas/sites_available.png)

Creamos un archivo de configuración para el dominio: <br> <br>
- sudo nano /etc/apache2/sites-available/departamento.centro.intranet.conf <br> <br>
![imagen](https://github.com/smordom/SREI/blob/main/1%C2%BA%20Trimestre/Trabajo%201%C2%BA%20Trimestre/Capturas/nano_departamento.png) <br>

Después de añadir los datos de virtualhost habilitamos el site <br>
- sudo a2ensite departamento.centro.intranet <br>
![imagen](https://github.com/smordom/SREI/blob/main/1%C2%BA%20Trimestre/Trabajo%201%C2%BA%20Trimestre/Capturas/a2ensite_departamentocentro.png) 

## 2. Activar los módulos necesarios para ejecutar php y acceder a mysql. <br> <br>

Instalamos MySQL con el comando: sudo apt install mysql-server

![imagen](https://github.com/smordom/SREI/blob/main/1%C2%BA%20Trimestre/Trabajo%201%C2%BA%20Trimestre/Capturas/install_mysql.png) <br> 

Y ejecutaremos el siguiente script por temas de seguridad: <br>

![imagen](https://github.com/smordom/SREI/blob/main/1%C2%BA%20Trimestre/Trabajo%201%C2%BA%20Trimestre/Capturas/mysql_secure.png) <br>

Luego comprobaremos con el comando "sudo mysql" que todo está funcionando: <br>

![imagen](https://github.com/smordom/SREI/blob/main/1%C2%BA%20Trimestre/Trabajo%201%C2%BA%20Trimestre/Capturas/sudo_mysql.png) <br>

Lo siguiente que haremos será installar PHP con el comando de la imagen: <br> 

![imagen](https://github.com/smordom/SREI/blob/main/1%C2%BA%20Trimestre/Trabajo%201%C2%BA%20Trimestre/Capturas/install_libapache.png) <br>

## 3. Instalación y configuración de WordPress. 

Iniciaremos sesión en mysql con  "mysql -u root -p"  permitiéndonos entrar como  usuario root. <br> 
PD: En mi caso he tenido que establecer una nueva contraseña con: <br> "ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'new_password';" <br>
Porque no me dejaba acceder. <br>
                                 
![imagen](https://github.com/smordom/SREI/blob/main/1%C2%BA%20Trimestre/Trabajo%201%C2%BA%20Trimestre/Capturas/sql_root.png)

Y crearemos una base de datos exclusiva para WordPress mediante: <br>

- "CREATE DATABASE wordpress DEFAULT CHARACTER SET utf8 COLLATE utf8_unicode_ci;" <br> 

![imagen](https://github.com/smordom/SREI/blob/main/1%C2%BA%20Trimestre/Trabajo%201%C2%BA%20Trimestre/Capturas/create_database.png)

Creamos un superusuario para la base de datos: <br>
- CREATE USER 'wordpressuser'@'%' IDENTIFIED WITH mysql_native_password BY
'password'; <br> <br> 
Damos todos los permisos <br>
- GRANT ALL ON wordpress.* TO 'wordpressuser'@'%'; <br> <br> 
Eliminamos privilegios para que MySQL sepa que cambios hemos realizado con: "FLUSH PRIVILEGES;"

![imagen](https://github.com/smordom/SREI/blob/main/1%C2%BA%20Trimestre/Trabajo%201%C2%BA%20Trimestre/Capturas/create_user.png) <br <br> 

Lo siguiente que haremos será utilizar un "apt get update" e instalaremos las extensiones de PHP: <br>
![imagen](https://github.com/smordom/SREI/blob/main/1%C2%BA%20Trimestre/Trabajo%201%C2%BA%20Trimestre/Capturas/install_phpcurl.png) <br> <br>

Ahora reiniciaremos apache y lo configuraremos para permitir .htaccess

![imagen](https://github.com/smordom/SREI/blob/main/1%C2%BA%20Trimestre/Trabajo%201%C2%BA%20Trimestre/Capturas/htaccess.png) <br> 
Y activamos el módulo rewrite <br> 
![imagen](https://github.com/smordom/SREI/blob/main/1%C2%BA%20Trimestre/Trabajo%201%C2%BA%20Trimestre/Capturas/enmod_rewrite.png)

Descargar WordPress <br> <br> <br>
Cambiamos de directorio que permita la escritura con "cd /tmp"<br>
Descargamos wordpress y lo instalamos con: <br><br>

- curl -O https://wordpress.org/latest.tar.gz
- tar xzvf latest.tar.gz <br>
Nota: Descargar en tmp puede dar errores, en mi caso he tenido que descargarlo en otra carpeta.

![imagen](https://github.com/smordom/SREI/blob/main/1%C2%BA%20Trimestre/Trabajo%201%C2%BA%20Trimestre/Capturas/instalar_wordpress.png) <br>

Ahora crearemos un archivo .htaccess para que wordpress pueda utilizarlo: 

![imagen](https://github.com/smordom/SREI/blob/main/1%C2%BA%20Trimestre/Trabajo%201%C2%BA%20Trimestre/Capturas/touch.png) <br>
Y copiamos el archivo de configuración de muestra al nombre del que lee
wordpress
- cp /tmp/wordpress/wp-config-sample.php /tmp/wordpress/wp-config.php <br>

![imagen](https://github.com/smordom/SREI/blob/main/1%C2%BA%20Trimestre/Trabajo%201%C2%BA%20Trimestre/Capturas/cp_wordpress.png)

Podemos crear el directorio de actualización para que wordpress no tenga problemas de permisos y copiamos el contenido de root de documentos: <br>
- mkdir /tmp/wordpress/wp-content/upgrade <br>
- sudo cp -a /tmp/wordpress/./var/www/centro.intranet <br> <br>

![imagen](https://github.com/smordom/SREI/blob/main/1%C2%BA%20Trimestre/Trabajo%201%C2%BA%20Trimestre/Capturas/mkdir_upgrade.png)
![imagen](https://github.com/smordom/SREI/blob/main/1%C2%BA%20Trimestre/Trabajo%201%C2%BA%20Trimestre/Capturas/cp_wordp_centrointranet.png) <br>

Actualizamos la propiedad del archivo: <br>

- sudo chown -R www-data:www-data /var/www/centro.intranet

Establecemos permisos correctos de los directorios y archivos de WordPress:

- sudo find /var/www/centro.intranet/ -type d -exec chmod 750 {} \;
- sudo find /var/www/centro.intranet/ -type f -exec chmod 640 {} \;

![imagen](https://github.com/smordom/SREI/blob/main/1%C2%BA%20Trimestre/Trabajo%201%C2%BA%20Trimestre/Capturas/chown_find.png)

## 4. Activación del módulo WSGI

Primero instalamos el modulo mediante: "sudo apt-get install libapache2-mod-wsgi-py" <br>
                                                                                       
![imagen](https://github.com/smordom/SREI/blob/main/1%C2%BA%20Trimestre/Trabajo%201%C2%BA%20Trimestre/Capturas/python_install.png)

Y creamos una estructura de directorios para nuestra aplicación:

![imagen](https://github.com/smordom/SREI/blob/main/1%C2%BA%20Trimestre/Trabajo%201%C2%BA%20Trimestre/Capturas/estructura_python.png) <br>


## 5. Crea y despliega una pequeña aplicación python para comprobar que funciona correctamente. 

Ahora creamos un controlador en nuestra carpeta de mypythonapp
![imagen](https://github.com/smordom/SREI/blob/main/1%C2%BA%20Trimestre/Trabajo%201%C2%BA%20Trimestre/Capturas/controller.py.png)
