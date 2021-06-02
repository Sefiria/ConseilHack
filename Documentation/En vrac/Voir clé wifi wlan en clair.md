# Voir clé wifi wlan en clair

1. Ouvrir le Command Line (Touche Windows > taper "cmd")
2. Taper cette instruction :

```
netsh wlan show profiles

3. Sélectionner dans la liste la cible (copier son nom)
4. Taper cette instruction (remplacer 'Cible' par le nom-cible copié):

```
netsh wlan show profiles Cible key=clear

5. Le mot de passe du wifi-cible est à la ligne "Contenu de la clé"
6. Vous pouvez vous connecter au réseau wifi ciblé avec le mot de passe récupéré