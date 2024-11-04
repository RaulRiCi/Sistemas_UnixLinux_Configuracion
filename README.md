# Laboratorio

## Fail2ban

Los siguientes comandos configuran y gestionan Fail2Ban, una herramienta de seguridad en Linux diseñada para prevenir ataques de fuerza bruta y otros intentos de acceso no autorizado. Fail2Ban funciona principalmente monitoreando los registros del sistema y tomando medidas cuando detecta actividad sospechosa, como múltiples intentos fallidos de inicio de sesión.

```apacheconf
sudo aptitude update
```

Actualiza los índices de los repositorios de paquetes usando aptitude. Es un paso redundante aquí, pero asegura que la información esté actualizada si fuera necesario instalar otros paquetes.

```apacheconf
sudo aptitude install fail2ban
```

Instala el paquete fail2ban usando el gestor de paquetes aptitude, que maneja dependencias de manera más interactiva y permite opciones avanzadas.

```apacheconf
cd /etc/fail2ban
```

Cambia el directorio de trabajo al de configuración de Fail2Ban (/etc/fail2ban).

```apacheconf
sudo cp jail.conf jail.local
```

Crea una copia de jail.conf con el nombre jail.local. Este archivo (jail.local) es donde se recomienda hacer modificaciones personalizadas de Fail2Ban, para que las actualizaciones del sistema no sobrescriban tus configuraciones.

```apacheconf
sudo nano jail.local
```

Abre el archivo jail.local en el editor de texto nano con permisos de superusuario para hacer ajustes. Aquí puedes configurar Fail2Ban, como qué servicios proteger (por ejemplo, SSH) y la duración de los bloqueos.

```apacheconf
cd
```

Cambia el directorio de trabajo de vuelta al directorio personal del usuario.

```apacheconf
sudo systemctl restart fail2ban
```

Reinicia el servicio Fail2Ban para aplicar cualquier cambio hecho en el archivo de configuración (jail.local).

```apacheconf
systemctl status fail2ban
```

Verifica nuevamente el estado de Fail2Ban después del reinicio.

```apacheconf
sudo systemctl start fail2ban
```

Inicia el servicio Fail2Ban si estaba detenido.

```apacheconf
sudo systemctl status fail2ban
```

Verifica nuevamente el estado del servicio Fail2Ban.

```apacheconf
sudo fail2ban-client status sshd
```

Consulta el estado del filtro de Fail2Ban para el servicio SSHD, mostrando estadísticas como IPs bloqueadas y tiempo de los bloqueos.

```apacheconf
sudo fail2ban-client set sshd unbanip [IP]
```

Desbloquea manualmente una dirección IP específica que había sido bloqueada para el servicio SSH.

```apacheconf
sudo fail2ban-client status sshd
```

Revisa nuevamente el estado de Fail2Ban en el servicio SSHD para verificar los cambios después de desbloquear una IP.

```apacheconf
sudo systemctl restart fail2ban.service
```

Reinicia el servicio Fail2Ban, asegurando que cualquier cambio o ajuste adicional se aplique correctamente.
