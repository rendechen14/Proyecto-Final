# Configuració del servidor

## Visió general
Aquest apartat descriu la instal·lació i posada en marxa dels principals serveis del servidor corporatiu.

La infraestructura s'ha desplegat sobre Ubuntu Server i inclou:
- servidor web Apache
- base de dades MariaDB
- suport per a PHP
- entorn de documentació amb MkDocs

## Actualització del sistema
Abans de la instal·lació dels serveis, s'actualitza el sistema operatiu:

```
sudo apt update
sudo apt upgrade -y
```

## Instal·lació del servidor web Apache
Apache s'utilitza com a servidor web principal:

```
sudo apt install apache2 -y
sudo systemctl enable apache2
sudo systemctl start apache2
sudo systemctl status apache2
```

## Instal·lació del sistema de base de dades MariaDB
MariaDB s'utilitza per a la gestió de la base de dades del sistema:

sudo apt install mariadb-server -y
sudo systemctl enable mariadb
sudo systemctl start mariadb
sudo systemctl status mariadb

## Instal·lació de PHP
PHP permet l'execució d'aplicacions web dinàmiques:

```
sudo apt install php libapache2-mod-php php-mysql -y
php -v
```

## Verificació del servei web
Per a comprovar el funcionament correcte del servidor web, es pot accedir a la IP del servidor des d'un navegador o executar:

```
curl http://localhost
```

## Instal·lació de MkDocs
MkDocs s'utilitza per a generar la documentació tècnica del projecte:

```
sudo apt install python3-pip -y
pip install mkdocs
pip install mkdocs-material
```

## Creació del projecte de documentació
Una vegada instal·lat MkDocs, es crea l'estructura base del portal de documentació:

```
mkdocs new SRE-Docs
cd SRE-Docs
mkdocs serve
```

## Resultat final
Després d'aquest procés, el servidor disposa dels serveis principals instal·lats i configurats, així com de l'entorn necessari per a mantindre la documentació tècnica del sistema.