# docs

**PHP**

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

Instalando PHP

```bash
sudo dnf module install php:remi-7.4
```
