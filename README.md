# LAMP en dos niveles
### Creamos los sh de arpivisonamiento de las dos maquinas virtuales
#### Script para MySQL
![](FOTOS/scriptsql.png)
#### Script para Apache2
![](FOTOS/scriptapache.png)
### Una vez creados los scripts, configuraremos el Vagrantfile agregando ambas maquinas y aplicando el aprovisionamiento
![](FOTOS/Vagrant.png)
### Una vez configurado todo, ponemos **vagrant up** y se empezaran a levantar ambas maquinas. Para comprobar que no han habido errores al iniciar las maquinas con el comando **vagrant status** podemos ver el estado de estas.
![](FOTOS/VagrantStatus.png)

# Configuracion MySQL
### Lo primero que hay que hacer es entrar en el directorio */etc/mysql/mariadb.conf.d* y ahí modificar el fichero *50-server.cnf*.
![](FOTOS/1.png)
### En este fichero cambiaremos la *bind-address* y pondremos la ip de nuestra maquina sql.
![](FOTOS/2.png)
### Ahora entramos a mysql como root y creamos un usuario con la ip de apache y le damos todos los permisos.
![](FOTOS/3.png)
### En el home de esta maquina volvemos a clonar el repositorio de git para poder descargar la base de datos.
![](FOTOS/4.png)
### Ahora entraremos a la carpeta creada y dentro de esta accederemos a db. Despues de esto en el fichero *database.sql* borraremos las ultimas 3 lineas y la aplicaremos a nuestro MySQL.
![](FOTOS/5.png)
### Una vez importada la base de datos podemos borrar la carpeta iaw-practica-lamp.
![](FOTOS/6.png)

# Configuracion APACHE
### Creamos una carpeta en */var/www* y le cambiamos el propietario con **chown**. Despues clonamos el repositorio de github con **git clone** y el enlace del repositorio que queremos usar.
![](FOTOS/1a.png)
### Entramos en la carpeta creada y dentro de esta entramos en *src*. Ahora movemos todo lo de esta carpeta a la carpeta que hemos creado en */var/www* y comprobamos que se hayan movido correctamente.
![](FOTOS/2a.png)
### Nos vamos a la carpeta de sites-available en */etc/apache2* y copiamos el fichero de configuración para modificarlo a nuestro gusto.
![](FOTOS/3a.png)
### Con sudo nano a el nuevo archivo de configuración ponemos la ruta de la carpeta que hemos creado en */var/www*.
![](FOTOS/4a.png)
### Ahora habilitamos el fichero de configuración con **a2ensite**. 
![](FOTOS/5a.png)
### Ahora nos vamos a */etc/apache2/sites-enabled* y desactivamos el fichero de configuración anterior con **a2dissite**. Despues de esto recargamos el apache2 con **sudo systemctl reload apache2**.
![](FOTOS/6a.png)
### Lo siguiente es entrar en la carpeta creada en */var/www* y editar el fichero config.php.
![](FOTOS/7a.png)
### En este fichero donde pone localhost ponemos la ip de la maquina de sql y cambiamos los datos de user y password.
![](FOTOS/8a.png)
### Instalamos el mysql-client con **sudo apt install -y default-mysql-client**.
![](FOTOS/9a.png)
### Ahora entramos a mysql con **mysql -u nombreusuario -p -h ipmysql**.
![](FOTOS/10a.png)
### Ahora si ponemos la dirección de la maquina de apache en Google saldrá la pagina del LAMP.
![](FOTOS/11a.png)
