## Práctica Servidores WEB      1º Trimestre

Instalación del servidor web apache Usaremos dos dominios mediante el archivo hosts: centro.intranet y departamentos.centro.intranet. El primero servirá el contenido mediante wordpress y el segundo una aplicación en python.

Actualizamos los repositorios con: “sudo apt update”

![imagen](https://github.com/smordom/SREI/blob/main/1%C2%BA%20Trimestre/Trabajo%201%C2%BA%20Trimestre/Capturas/sudo_apt_update.png)

Procedemos a instalar apache2 mediante el siguiente comando: sudo apt install apache2

![imagen](https://github.com/smordom/SREI/blob/main/1%C2%BA%20Trimestre/Trabajo%201%C2%BA%20Trimestre/Capturas/sudo_apt_install_apache2.png)

Ajustaremos el firewall para permitir el tráfico web y permitiremos a Apache: 

sudo ufw app list
sudo ufw app info “Apache Full”
sudo ufw allow “Apache Full”

![imagen](https://github.com/smordom/SREI/blob/main/1%C2%BA%20Trimestre/Trabajo%201%C2%BA%20Trimestre/Capturas/ufw_app_list.png)
