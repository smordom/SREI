## Práctica Servidores WEB      1º Trimestre

Instalación del servidor web apache Usaremos dos dominios mediante el archivo hosts: centro.intranet y departamentos.centro.intranet. El primero servirá el contenido mediante wordpress y el segundo una aplicación en python.

Actualizamos los repositorios con: “sudo apt update”

![imagen](https://github.com/smordom/SREI/blob/main/1%C2%BA%20Trimestre/Trabajo%201%C2%BA%20Trimestre/Capturas/sudo_apt_update.png)

Procedemos a instalar apache2 mediante el siguiente comando: sudo apt install apache2

![imagen](https://github.com/smordom/SREI/blob/main/1%C2%BA%20Trimestre/Trabajo%201%C2%BA%20Trimestre/Capturas/sudo_apt_install_apache2.png)

Ajustaremos el firewall para permitir el tráfico web y permitiremos a Apache: 

sudo ufw app list <br>
sudo ufw app info “Apache Full” <br>
sudo ufw allow “Apache Full” <br>

![imagen](https://github.com/smordom/SREI/blob/main/1%C2%BA%20Trimestre/Trabajo%201%C2%BA%20Trimestre/Capturas/ufw_app_list.png)

Y con esto ya tendríamos listo apache y funcionando: 

![imagen](https://github.com/smordom/SREI/blob/main/1%C2%BA%20Trimestre/Trabajo%201%C2%BA%20Trimestre/Capturas/apache_funcionando.png)

Reiniciamos apache server con: sudo systemctl restart apache2 <br>
Y comprobaremos  su estado con: sudo systemctl status apache2 

![imagen](https://github.com/smordom/SREI/blob/main/1%C2%BA%20Trimestre/Trabajo%201%C2%BA%20Trimestre/Capturas/reiniciar_sistema.png)

Añadir el dominio “centro.intranet” y “departamento.centro.intranet” en el fichero “host” con "nano /etc/hosts" y añadiremos lo siguiente: <br>

127.0.0.1 centro.intranet <br>
127.0.0.1 departamento.centro.intranet

![imagen](https://github.com/smordom/SREI/blob/main/1%C2%BA%20Trimestre/Trabajo%201%C2%BA%20Trimestre/Capturas/url_centrointranet.png)

Creamos un archivo de configuración para el dominio: <br>
sudo nano /etc/apache2/sites-available/centro.intranet.conf <br>
Después de añadir los datos de virtualhost habilitamos el site "sudo a2ensite centro.intranet"

![imagen](https://github.com/smordom/SREI/blob/main/1%C2%BA%20Trimestre/Trabajo%201%C2%BA%20Trimestre/Capturas/nano_centrointranet.png)

![imagen](https://github.com/smordom/SREI/blob/main/1%C2%BA%20Trimestre/Trabajo%201%C2%BA%20Trimestre/Capturas/sites_available.png)

Creamos un archivo de configuración para el dominio: <br> <br>
    sudo nano /etc/apache2/sites-available/departamento.centro.intranet.conf <br> <br>
![imagen](https://github.com/smordom/SREI/blob/main/1%C2%BA%20Trimestre/Trabajo%201%C2%BA%20Trimestre/Capturas/nano_departamento.png) <br>

Después de añadir los datos de virtualhost habilitamos el site <br>
sudo a2ensite departamento.centro.intranet
![imagen](https://github.com/smordom/SREI/blob/main/1%C2%BA%20Trimestre/Trabajo%201%C2%BA%20Trimestre/Capturas/a2ensite_departamentocentro.png)

2. Activar los módulos necesarios para ejecutar php y acceder a mysql. <br> <br>

Instalamos MySQL con el comando: sudo apt install mysql-server
