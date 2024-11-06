author: Carlos Cordero Moreno
summary: Una guía para bastionar el arranque en Debian
id: 2
categories: codelab,markdown,debian,bastionar,seguro
environments: Web
status: Published

# Proyecto 1.2

## Introducción
Duration: 00:01:00

En este tutorial vamos a aprender a como bastionar el arranque de un sistema de Debian
![grub](/images/arranque_de_grub-1.webp)

## Arranque con contraseña
Duration 00:02:00

En este paso vamos a ver como proteger el arranque con una contraseña.
Para ello desde una terminal ejecutamos como usuario root o con sudo el siguiente comando <code>sudo nano /etc/grub.d/40_custom</code>
![comandopasswd](/images/debian3.png)
Una vez abierto el archivo ponemos al final del mismo este codigo, siendo contraseña la que queremos establecer:
```
set superusers=“root”
password root contraseña
```
![40_custom](/images/debian5.png)

Para actualizar los cambios ejecutamos <code>sudo update-grub</code>
## Cifrado de contraseña de arranque
Duration 00:02:00

Para cifrar la contraseña ponemos este comando para generarla <code>sudo grub-mkpasswd-pbkdf2</code>

![40_custom](/images/debian10.png)

Copiamos la respuesta y la ponemos en el mismo archivo de antes, sustituyendo password por password_pbkdf2, deberia de quedar así:

![40_custom](/images/debian11.png)

Para actualizar los cambios ejecutamos <code>sudo update-grub</code>

Para editar los permisos del archivo para que solo lo pueda editar root, introducimos el siguiente comando <code>sudo chmod 700 /etc/grub.d/40_custom</code>

## Ocultar menú de arranque
Duration 00:02:00

Abrimos el archivo /etc/default/grub con el siguiente comando <code>nano /etc/default/grub</code> y cambiamos GRUB_TIMEOUT=5 a GRUB_TIMEOUT=0.

![40_custom](/images/debian14.png)

Y solo faltaría volver a actualizar el grub con <code>sudo update-grub</code>