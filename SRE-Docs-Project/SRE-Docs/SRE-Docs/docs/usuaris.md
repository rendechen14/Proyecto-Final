# Gestió de rols i usuaris

## Visió general
Per a garantir una administració ordenada i segura del servidor, s'han definit diferents usuaris amb funcions específiques.

L'assignació de permisos s'ha realitzat aplicant el principi de mínim privilegi, de manera que cada usuari només disposa dels accessos necessaris per a la seua funció.

## Usuari root
L'usuari `root` és l'administrador principal del sistema.

### Funcions
- Control total del servidor
- Instal·lació i eliminació de paquets
- Gestió de serveis i configuracions
- Administració completa d'usuaris i permisos

## Usuari admin-web
L'usuari `admin-web` està destinat a la gestió del servidor web i dels fitxers associats al servei Apache.

### Funcions
- Editar fitxers del lloc web
- Gestionar contingut web
- Reiniciar o comprovar l'estat del servidor Apache
- Supervisar configuracions bàsiques del servei web

### Exemple de creació
sudo adduser admin-web
sudo usermod -aG www-data admin-web

## Usuari db-backup
L'usuari `db-backup` està destinat a la realització de còpies de seguretat de la base de dades.

### Funcions
- Exportar bases de dades
- Guardar còpies de seguretat
- Organitzar fitxers de backup
- No modificar la configuració del servidor web

### Exemple de creació
sudo adduser db-backup

## Usuari auditor
L'usuari `auditor` s'utilitza per a tasques de revisió i supervisió del sistema.

### Funcions
- Consultar registres del sistema
- Revisar intents d'accés
- Supervisar logs d'Apache i d'autenticació
- Detectar incidències de seguretat o errors de configuració

## Política de permisos
La gestió d'usuaris s'ha plantejat amb una distribució clara de responsabilitats:
- `root`: administració global del sistema
- `admin-web`: gestió del servei web
- `db-backup`: còpies de seguretat de base de dades
- `auditor`: revisió de logs i supervisió

Aquesta distribució millora la seguretat, facilita l'organització del treball i redueix el risc d'errors o accessos no autoritzats.