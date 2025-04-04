# Resumen

En los sistemas GNU/Linux es común el uso de archivos de configuración que comúnmente se mantienen ocultos en el *home* del usuario o en las subcarpetas *config* o *local*. Estas configuraciones mantienen los parámetros establecidos por el usuario final y a menudo suelen usarse cuando se reinstala un sistema operativo GNU/Linux.

En esta guía pretende explicar los pasos a seguir para configurar un entorno de escritorio a partir de un sistema base, esto es, un sistema limpio con los paquetes básicos y necesarios para hacer funcionar el sistema operativo en nuestro equipo de cómputo. El sistema operativo para realizar esta tarea será Debian. Posteriormente, se pretende que el *script* que instala los *dotfiles* de este repositorio pueda funcionar en otras distribuciones como Arch Linux, OpenSuse o Fedora las cuales trabajan con otros tipos de gestores de paquetes y leves modificaciones en la estructura de las configuraciones en el *home*.


# Instalación de Debian

Las configuraciones de este repositorio están diseñadas para una instalación básica del sistema operativo Debian. El archivo ISO denominado *netinstall* con el instalador de la distribución mencionada se puede obtener de la página oficial del proyecto Debian. En la siguiente lista de reproducción se encuentra una explicación de la instalación del sistema operativo Debian en modo dual con Windows 11. El resultado final de la operación es la esperada para poder hacer funcionar los *dotfiles*.

[https://www.youtube.com/watch?v=x-O5anHdti8&list=PLkDJCdY1Fr9WbXWXLmCUYq6kb9W52P2V6]( https://www.youtube.com/watch?v=x-O5anHdti8&list=PLkDJCdY1Fr9WbXWXLmCUYq6kb9W52P2V6)

Con el sistema operativo base funcionando, es necesario instalar un par de paquetes en el sistema, esto en Debian por medio del usuario root escribiendo el comando.

    su -

Para mantener una instalación limpia, sin paquetes adicionales e innecesarios, se debe indicar al comando **apt** el parametro **--no-install-recommends**. Los comandos a instalar son los siguientes.

    apt install --no-install-recommends xorg xserver-xorg lightdm network-manager network-manager-gnome i3 i3status gnome-terminal nemo dmenu rofi firefox-esr git

La lista de paquetes anteriores permite la funcionalidad del sistema base. Es importante estar familiarizados con los gestores de ventanas en GNU/Linux. La configuración del entorno de escritorio usa el gestor de ventanas i3. El manual para entender su funcionalidad se puede leer en el siguiente enlace.

[https://i3wm.org/docs/userguide.html](https://i3wm.org/docs/userguide.html)


# Instalación de los archivos de configuración

Desde una terminal y desde cualquier ubicación en el sistema de archivos, clonamos el repositorio.

    git clone https://github.com/lexbaalam/gnu-dotfiles.git

Suponiendo que la clonación del repositorio se hizo en la ruta ~/usuario/documentos/proyectos/gnu-dotfiles, el enlace simbólico al home del usuario se establecería con el siguiente comando

ln -sd ~/usuario/documentos/proyectos/gnu-dotfiles ~/usuario/.dotfiles

Desde el *home* del usuario entramos a la carpeta del enlace simbólico 

    cd ~/.dotfiles

Se instalarán todos los paquetes que requieren los *scripts* contenidos en la carpeta local que se encuentran en los *dotfiles* usando el comando.

    su root -- -c 'bash dotinstall -g' o su root -- -c 'bash dotinstall --getapps'

Después de instalar los paquetes con el comando anterior, se debe ejecutar el siguiente comando que establecerá las configuraciones del entorno de escritorio.

    bash dotinstall -i o bash dotinstall --install


Las funcionalidades del entorno se pueden ver en el archivo de configuración de i3 que se encuentra en la carpeta *config*.
