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

Ahora instalaremos PHP: 
![imagen](https://user-images.githubusercontent.com/72253934/221396028-e98ec48b-af6c-413f-a6ec-b5fa6b7ed89f.png) <br>

2. Los clientes dispondrán de un directorio de usuario con una página web
por defecto. <br>

En la carpeta HTML crearemos una carpeta de usuario con un index.html para que tenga una página web diferente a la de por defecto. <br>
Al haber instalado php tambien podríamos añadir una página dinámica.
![imagen](https://user-images.githubusercontent.com/72253934/221397684-a418f428-81c0-4356-959b-03a493f7d51c.png) <br>
![imagen](https://user-images.githubusercontent.com/72253934/221397697-5155bbcd-6d20-484c-9900-d7532b2b5033.png)
