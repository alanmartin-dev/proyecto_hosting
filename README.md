 Auto Provisionador de Usuarios Web (Bash + Nginx + MariaDB)

Este proyecto es un script en Bash que automatiza la creación de entornos web individuales por usuario en un servidor Linux.
Está pensado para escenarios como hosting local, prácticas académicas o entornos de laboratorio.

Con un solo script puedes generar:

Usuario del sistema
Directorio web (public_html)
Sitio web inicial (HTML + PHP)
Base de datos en MariaDB
Configuración de Nginx con subdominio
Credenciales listas para uso
⚙️ Características

- Generación automática de usuarios (usuario01, usuario02, ...)
- Contraseñas seguras generadas con OpenSSL
- Virtual Hosts en Nginx por usuario
- Soporte PHP (php-fpm)
- Base de datos independiente por usuario
- Estructura web lista (public_html)
- Página inicial con diseño personalizado (incluye pingüino 😎)
- Restricción de acceso SSH (enjaulado básico)

🧱 Estructura generada

Cada usuario tendrá:

/home/usuarioXX/
├── public_html/
│   ├── index.html
│   ├── credenciales.html
│   └── info.php
🚀 Requisitos

Antes de ejecutar el script, asegúrate de tener instalado:

Linux (Ubuntu/Debian recomendado)
nginx
mariadb-server
php + php-fpm
openssl

Instalación rápida (Ubuntu):

sudo apt update
sudo apt install nginx mariadb-server php php-fpm openssl -y
▶️ Uso
Clona el repositorio o guarda el script:
chmod +x script.sh
Ejecuta el script:
./script.sh
El sistema mostrará:
- Usuario creado: usuario01
- Contraseña: xxxxxxxx
- Carpeta: /home/usuario01
- http://usuario01.com
- Acceso al sitio

El script configura automáticamente un dominio local:

http://usuarioXX.com

⚠️ Nota: Esto funciona dentro de la máquina o entorno donde se ejecuta (usa /etc/hosts).

🗄️ Base de Datos

Por cada usuario se crea:

Base de datos: usuarioXX
Usuario: usuarioXX
Contraseña: (la misma generada)

Acceso mediante:

http://<IP>:8018/phpmyadmin
🔐 Seguridad
Usuarios con acceso SSH restringido (/usr/sbin/nologin)
Se añade a DenyUsers en configuración SSH
Permisos de directorio controlados (755)

- Importante: Este script es para entornos controlados.
