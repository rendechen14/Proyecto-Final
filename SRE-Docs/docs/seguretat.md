# Hardening del servidor

## Visió general
Per a reforçar la protecció del sistema, s'han aplicat diverses mesures bàsiques de hardening orientades a reduir el risc d'accessos no autoritzats i millorar la seguretat general del servidor.

## Canvi del port SSH
Per defecte, el servei SSH utilitza el port 22. Per a reduir intents automàtics de connexió, s'ha modificat el port per defecte.

### Fitxer de configuració

```
sudo nano /etc/ssh/sshd_config
```

### Exemple de configuració de un port alternatiu

```
Port 2222
```

### Reinici del servei

```
sudo systemctl restart ssh
```

## Desactivació de l'accés directe de root per SSH
Per a evitar accessos remots insegurs amb privilegis totals, s'ha desactivat l'inici de sessió directe de `root`.

### Per aixo se ha de posar

```
PermitRootLogin no
```

## Configuració del tallafocs amb UFW
S'ha configurat un firewall per a permetre únicament els ports necessaris per al funcionament del servidor.

```
sudo apt install ufw -y
sudo ufw allow 2222/tcp
sudo ufw allow 80/tcp
sudo ufw allow 443/tcp
sudo ufw enable
sudo ufw status
```

## Actualització del sistema
Es manté el sistema actualitzat per a corregir vulnerabilitats i aplicar millores de seguretat:

```
sudo apt update
sudo apt upgrade -y
```

## Còpies de seguretat
S'han previst còpies de seguretat periòdiques per a protegir la informació crítica del sistema i de la base de dades.

### Exemple de còpia de seguretat

```
mysqldump -u root -p basededades > copia.sql
```

## Revisió de logs
La revisió periòdica de registres permet detectar accessos sospitosos, errors de servei i possibles incidències de seguretat.

### Exemples de consulta

```
sudo cat /var/log/auth.log
sudo cat /var/log/apache2/access.log
sudo cat /var/log/apache2/error.log
```

## Conclusions
Les mesures aplicades milloren la protecció del servidor, limiten la superfície d'exposició i faciliten la supervisió del sistema en entorns corporatius.