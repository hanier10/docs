**Instalando PHP 7.4 y Valet en Fedora 35**

**Instalación de PHP**

---

Agregando repositorio Remi

```bash
sudo dnf -y install https://rpms.remirepo.net/fedora/remi-release-35.rpm
```

Algunas dependencias comunes están disponibles en el repositorio de remi, que deben habilitarse:

```bash
sudo dnf config-manager --set-enabled remi
```

```bash
sudo  dnf module reset php
```

Instalando PHP 7.4:

```bash
sudo dnf module install php:remi-7.4
```

Instalando dependencias:

```bash
sudo dnf install php-fpm php-cli php-curl php-mbstring php-xml php-zip php-pgsql php-gd php-soap php-json
```

Actualizamos:

```bash
sudo dnf update
```

Verificar la versión de PHP

```bash
php -version
```

**Instalación de Composer** (Antes de instalar Composer asegúrese de tener instalado PHP correctamente)

---

```bash
sudo apt-get install curl
```

```bash
curl -sS https://getcomposer.org/installer | php
```

```bash
sudo mv ~/composer.phar /usr/local/bin/composer
```

**Instalación de Valet**

---

```bash
composer global require cpriego/valet-linux
```

Agregando la variable de entorno

```bash
export PATH="$PATH:$HOME/.config/composer/vendor/bin"
```

Recargar bashrc

```bash
source .bashrc
```

Activar el modo permisivo de manera permanente, accederemos al siguiente archivo:

```bash
sudo nano /etc/selinux/config
```

Al acceder en el archivo anterior, modificar de la siguiente manera:

```bash
SELINUX=permissive
```

Guardar cambios (Ctrl + O y luego enter) y salir (Ctrl + X).

Ejecutar el siguiente comando:

```bash
valet install
```

Si en el comando anterior pide instalar algunas dependencias, ejecutar lo siguiente:

```bash
sudo dnf install nss-tools jq xsel
```

```bash
sudo dnf install php-{cli,process,mbstring,mcrypt,xml}
```

Luego de instaladas las dependencias ejecutar nuevamente *valet install*

Solo si por alguna razón te quedas sin internet, ejecuta los siguientes comandos:

```bash
sudo systemctl start systemd-resolved
```

```bash
sudo systemctl enable systemd-resolved
```

```bash
sudo systemctl restart NetworkManager
```

Ahora vamos a crear una carpeta en el directorio raíz preferiblemente de nuestro equipo, en donde tendremos alojados nuestros proyectos de Laravel:

```bash
cd

mkdir Site

cd Site

valet park
```

Levantamos valet

```bash
valet start
```

Dentro de nuestra carpeta Site ejecutamos el siguiente comando:

```bash
valet park
```

Puedes verificar el estado de valet con

```bash
valet status
```
