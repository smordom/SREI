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

Ahora contruimos nuestras estadísticas con:
- sudo /usr/lib/cgi-bin/awstats.pl -config=centro.intranet -update
- sudo /usr/lib/cgi-bin/awstats.pl -config=departamento.centro.intranet -update
## 4. Activación del módulo WSGI

Primero instalamos el modulo mediante: "sudo apt-get install libapache2-mod-wsgi-py" <br>
                                                                                       
![imagen](https://github.com/smordom/SREI/blob/main/1%C2%BA%20Trimestre/Trabajo%201%C2%BA%20Trimestre/Capturas/python_install.png)

Y creamos una estructura de directorios para nuestra aplicación:

![imagen](https://github.com/smordom/SREI/blob/main/1%C2%BA%20Trimestre/Trabajo%201%C2%BA%20Trimestre/Capturas/estructura_python.png) <br>


## 5. Crea y despliega una pequeña aplicación python para comprobar que funciona correctamente. 

Ahora creamos un controlador en nuestra carpeta de mypythonapp: <br>

![imagen](https://github.com/smordom/SREI/blob/main/1%C2%BA%20Trimestre/Trabajo%201%C2%BA%20Trimestre/Capturas/controller.py.png) <br>

Y configuramos el fichero host con lo siguiente: <br>

![imagen](https://github.com/smordom/SREI/blob/main/1%C2%BA%20Trimestre/Trabajo%201%C2%BA%20Trimestre/Capturas/nano_pythondepart.png) <br>

Y reiniciamos apache.

## 6. Añadir protección de acceso a la aplicación python mediante autentificación.

Creamos directorio donde guardar la contraseña y un archivo donde guardarla la contraseña con el comando: <br>

- sudo htpasswd -c /usr/local/apache/passwd/password usuario

![imagen](https://github.com/smordom/SREI/blob/main/1%C2%BA%20Trimestre/Trabajo%201%C2%BA%20Trimestre/Capturas/crear_contrase%C3%B1a.png)

Ahora configuraremos el servidor que queramos nos pregunte la contraseña y tengan acceso solo los usuarios que queramos, editando el archivo apache2.conf.

![imagen](https://github.com/smordom/SREI/blob/main/1%C2%BA%20Trimestre/Trabajo%201%C2%BA%20Trimestre/Capturas/conf_contrase%C3%B1a.png)


## 7. Instalación y configuración de AWSTATS.

Instalamos el paquete awstats con el comando:

![imagen](https://github.com/smordom/SREI/blob/main/1%C2%BA%20Trimestre/Trabajo%201%C2%BA%20Trimestre/Capturas/aptget_awstats.png) <br>

Y también habilitamos el módulo CGI en Apache:

- sudo a2enmod cgi

Ahora creamos el archivo de configuración para cada dominio, en este caso copiando los existentes: 

![imagen](https://github.com/smordom/SREI/blob/main/1%C2%BA%20Trimestre/Trabajo%201%C2%BA%20Trimestre/Capturas/cp_awstats.png)

Ahora editamos los archivos y añadimos lo siguiente: 

![imagen](https://github.com/smordom/SREI/blob/main/1%C2%BA%20Trimestre/Trabajo%201%C2%BA%20Trimestre/Capturas/awstats_centro.png) <br>

![imagen](https://github.com/smordom/SREI/blob/main/1%C2%BA%20Trimestre/Trabajo%201%C2%BA%20Trimestre/Capturas/awstats_departamento.png) <br>

Y luego añadiremos en ambos:

![imagen](https://github.com/smordom/SREI/blob/main/1%C2%BA%20Trimestre/Trabajo%201%C2%BA%20Trimestre/Capturas/updatestats.png)

Ahora contruimos nuestras estadísticas con:
- sudo /usr/lib/cgi-bin/awstats.pl -config=centro.intranet -update
- sudo /usr/lib/cgi-bin/awstats.pl -config=departamento.centro.intranet -update

![imagen](https://github.com/smordom/SREI/blob/main/1%C2%BA%20Trimestre/Trabajo%201%C2%BA%20Trimestre/Capturas/estadisticas.png)

Configuramos Apache2 para que muestre estas estadísticas. Copiamos el contenido de la carpeta «cgi-bin» en el directorio raíz del documento por defecto de su instalación de Apache.

- sudo cp -r /usr/lib/cgi-bin /var/www/html/
- sudo chown www-data:www-data /var/www/html/cgi-bin/
- sudo chmod -R 755 /var/www/html/cgi-bin/

![imagen](https://github.com/smordom/SREI/blob/main/1%C2%BA%20Trimestre/Trabajo%201%C2%BA%20Trimestre/Capturas/cgibin.png) <br> 

Una vez hecho esto se pueden acceder a los stats poniendo en el navegador:
- http://127.0.0.1/cgi-bin/awstats.pl?config=centro.intranet
- http://127.0.0.1/cgi-bin/awstats.pl?config=departamento.centro.intranet

![imagen](https://github.com/smordom/SREI/blob/main/1%C2%BA%20Trimestre/Trabajo%201%C2%BA%20Trimestre/Capturas/stadistics.png)

## 8. Instala un segundo servidor de tu elección (nginx, lighttpd) bajo el dominio “servidor2.centro.intranet”. Debes configurarlo para que sirva en el puerto 8080 y haz los cambios necesarios para ejecutar php. Instala phpmyadmin.


En primer lugar procederemos a instalar el servidor que hayamos elegido: 

![imagen](https://github.com/smordom/SREI/blob/main/1%C2%BA%20Trimestre/Trabajo%201%C2%BA%20Trimestre/Capturas/install_nginx.png) <br>

Daremos permiso al menos restrictivo: 

![imagen](https://github.com/smordom/SREI/blob/main/1%C2%BA%20Trimestre/Trabajo%201%C2%BA%20Trimestre/Capturas/ngix%20http.png) <br>

Y crearemos el dominio y cambiaremos los permisos:

![imagen](https://github.com/smordom/SREI/blob/main/1%C2%BA%20Trimestre/Trabajo%201%C2%BA%20Trimestre/Capturas/cosas%20multiples.png)

Y haremos un pequeño index para nuestro servidor: 

![imagen](https://github.com/smordom/SREI/blob/main/1%C2%BA%20Trimestre/Trabajo%201%C2%BA%20Trimestre/Capturas/index%20nginex.png)

Ahora crearemos el archivo de configuración y lo habilitaremos haciendo un enlace entre él y el directorio "sites-enable": 

![imagen](https://github.com/smordom/SREI/blob/main/1%C2%BA%20Trimestre/Trabajo%201%C2%BA%20Trimestre/Capturas/nginx%20sites.png)

Para evitar errores abrimos y modificamos "sudo nano /etc/nginx/nginx.conf", quitando la almohadilla donde la captura:

![imagen](https://github.com/smordom/SREI/blob/main/1%C2%BA%20Trimestre/Trabajo%201%C2%BA%20Trimestre/Capturas/server_names.png)

Comprobamos que no haya errores de sintaxis: 

![imagen](https://github.com/smordom/SREI/blob/main/1%C2%BA%20Trimestre/Trabajo%201%C2%BA%20Trimestre/Capturas/sintax.png)

Y ahora pasaremos a configurar PHP en nuestro servidor: 

![imagen](https://github.com/smordom/SREI/blob/main/1%C2%BA%20Trimestre/Trabajo%201%C2%BA%20Trimestre/Capturas/config_php.png)

Aceptaremos todo y le estableceremos la contraseña que querramos. <br>

Creamos un enlace con:
- sudo ln -s /usr/share/phpmyadmin /var/www/servidor2.centro.intranet/phpmyadmin <br>
 Y con esto solo tenemos que dirigirnos a la dirección de nuestra página WEB y ya estaría acabado
 
 ![imagen](https://github.com/smordom/SREI/blob/main/1%C2%BA%20Trimestre/Trabajo%201%C2%BA%20Trimestre/Capturas/y_ya.png)
