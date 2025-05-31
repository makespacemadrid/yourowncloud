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
- Instalar Docker:

```
    curl -fsSL https://get.docker.com -o get-docker.sh
    sh get-docker.sh
    sudo apt install docker-compose-plugin
```


  
- Clonar el repo
- Configurar la llave del dyndns en la configuracion
- Levantar el stack de proxy reverso
- Comprobar que todos los servicios funcionan correctamente.
- Configuracion inicial del proxy (subdominios de gestion, estadisticas y kuma)
- Levantar resto de servicios



🔐 Buenas prácticas y seguridad
Al autoalojar servicios en casa, no solo importa que funcionen, sino que lo hagan de forma segura y sostenible. Aquí algunos consejos clave:

1. 🌐 Wildcard DNS y SSL
Wildcard DNS: Crea una entrada *.midominio.xyz para apuntar todos los subdominios a tu IP. Así puedes añadir servicios sin tener que tocar el panel del dominio cada vez.

Certificado SSL Wildcard: Emite un único certificado Let’s Encrypt para *.midominio.xyz. Esto evita exponer tus subdominios individuales en los registros públicos de certificados (CT logs).

Puedes automatizarlo con Nginx Proxy Manager o certbot + DNS challenge.

2. 🔁 Actualizaciones automáticas
Sistema operativo:

Activa actualizaciones automáticas críticas o periódicas (por ejemplo, cada 2 semanas).

En Debian/Ubuntu:

    sudo apt install unattended-upgrades
    sudo dpkg-reconfigure --priority=low unattended-upgrades
Contenedores:

Usa Watchtower para actualizar imágenes Docker automáticamente.

Ejemplo en docker-compose.yml:


watchtower:
  image: containrrr/watchtower
  volumes:
    - /var/run/docker.sock:/var/run/docker.sock
  environment:
    - WATCHTOWER_CLEANUP=true
    - WATCHTOWER_POLL_INTERVAL=86400  # cada 24h

3. 🔒 Seguridad de acceso
Evita exponer servicios innecesarios: Usa redes privadas, VPNs como Tailscale o Zerotier.

Protege interfaces como Nginx Proxy Manager, phpMyAdmin, Portainer...

Usa contraseñas fuertes y verifica que solo están accesibles desde tu IP o por VPN.

Fail2ban o iptables para proteger puertos si los expones.
