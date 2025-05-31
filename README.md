# Your Own Cloud
Taller de self hosting

🏠 Tu nube, tus reglas.
Levanta tus propios servicios en casa con dominio propio, Docker y un proxy inverso.

🧠 Objetivo
Entender como funcionan las peticiones web, aprender a registrar un dominio, apuntarlo a tu casa con DNS dinámico, y levantar una infraestructura básica para servicios personales como WordPress, Nextcloud, Bitwarden, Jitsi o Home Assistant usando Docker Compose.

Taller:
- Registra un dominio
- entrada @ tipo dns dinamico
- cname de * a @
- Configurar en el router el nat para los puertos 80 y 443
- Instalar Docker
- Clonar el repo
- Configurar la llave del dyndns en la configuracion
- Levantar el stack de proxy reverso
- Comprobar que todos los servicios funcionan correctamente.
- Configuracion inicial del proxy (subdominios de gestion, estadisticas y kuma)
- Levantar Wordpress
