# Voir cl� wifi wlan en clair

1. Ouvrir le Command Line (Touche Windows > taper "cmd")
2. Taper cette instruction :

```
netsh wlan show profiles

3. S�lectionner dans la liste la cible (copier son nom)
4. Taper cette instruction (remplacer 'Cible' par le nom-cible copi�):

```
netsh wlan show profiles Cible key=clear

5. Le mot de passe du wifi-cible est � la ligne "Contenu de la cl�"
6. Vous pouvez vous connecter au r�seau wifi cibl� avec le mot de passe r�cup�r�