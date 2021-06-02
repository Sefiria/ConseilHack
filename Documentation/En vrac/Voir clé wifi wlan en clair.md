# Voir clé wifi wlan en clair

1. Ouvrir le Command Line (Touche Windows > taper "cmd")
2. Taper cette instruction :
```
netsh wlan show profiles
```
3. Sélectionner dans la liste la cible (copier son nom)
4. Taper cette instruction (remplacer 'Cible' par le nom-cible copié) :
```
netsh wlan show profiles Cible key=clear
```
5. Le mot de passe du wifi-cible est à la ligne "Contenu de la clé"
6. Vous pouvez vous connecter au réseau wifi ciblé avec le mot de passe récupéré

# Erreur(s) connue(s) :

Si le message suivant apparaît :
```
Le service Configuration automatique des réseaux locaux sans fil (wlansvc)
n'est pas en cours d'exécution.
```
Cela signifie que votre PC n'est pas doté d'une carte WiFi (vous ne pouvez pas récupérer / vous connecter à un réseau WiFi).
Ou bien, que celle-ci est désactivée (ce qui arrive lorsque l'on est connecté par filaire - ethernet).