# Récupérer IP peer depuis navigateur (omegle, Bazoocam, chatroulette...)

## Récupérer l'IP

Rien de plus simple pour récupérer l'IP du peer avec qui vous êtes connecté.  
Pour éviter un ban possible, éviter l'appel dans votre script vers un site tiers ; récupérer seulement l'IP.

1. Ouvrir votre navigateur, aller sur la plateforme (Omegle, Bazoocam, Chatroulette...)
2. Ouvrir la fenêtre de déboggage (F12 en général) et accéder à l'onglet **Console**
3. Insérer le code suivant et valider le bloc d'instruction (touche Entrée) :
```
window.oRTCPeerConnection  = window.oRTCPeerConnection || window.RTCPeerConnection
window.RTCPeerConnection = function(...args) {
const pc = new window.oRTCPeerConnection(...args)
pc.oaddIceCandidate = pc.addIceCandidate
pc.addIceCandidate = function(iceCandidate, ...rest) {
 const fields = iceCandidate.candidate.split(' ')
if (fields[7] === 'srflx') {
console.log('IP Address:', fields[4])
}
return pc.oaddIceCandidate(iceCandidate, ...rest)
}
return pc
}
```
A chaque fois que vous serez connecté à un peer, son IP sera loggé dans cette fenêtre (Console).  

## Tracer son IP pour connaître sa ville actuelle exacte

En amont, vous devez aller sur *ipinfo.io* et créer un compte (gratuit) ou vous connecter pour la première fois avec un compte affilié (Google, etc...).  
Ceci fait, vous devez valider votre compte (mail de validation).  
Ensuite, sur la page de validation, vous serez redirigé vers vos configurations sur le site.  
Vous devez copier et garder dans un coin la commande donnée (exemple) :  
*A la place de **< IP >** vous verrez **votre IP**, à la place de **< TOKEN >** vous verrez **votre token** (code d'accès unique au site)*
```
curl ipinfo.io/<IP>\?token=<TOKEN>
```
Préparez aussi un terminal (cmd, powershell...) à côté.  

1. Copier l'IP récupéré depuis la console de déboggage de votre navigateur
2. Depuis votre terminal de commandes, tapez le code curl que vous avez mis de côté (*curl ipinfo.io/92.168.92.8\?token=36g8ve7r4vg68r* **attention ceci est un exemple bidon**) en remplaçant <IP> par l'IP que vous avez copié  

Félicitations ! Vous venez de récupérer l'IP de votre peer, et vous avez trouvé sa géolocalisation (ville, région, pays) !  
Comprenez que vous n'êtes jamais vraiment anonyme sur internet.  
Restez vigilants.  

## VPN : sécurisé, mais pas complètement anonyme

Le cas du VPN actif ne vous anonymise pas pour autant.  
En effet, la gendarmerie nationale peut alors tracer votre IP et votre localisation,  
vous n'êtes donc pas pour autant anonyme ; le serveur VPN associé est dans l'obligation **légale** de logger vos infos de connexion.  
Dans le cas d'une procédure pénale il sera demandé au fournisseur VPN de divulguer votre identité.  
(Dans le cas où le fournisseur n'est pas en mesure de fournir ces informations, il sera alors tenu responsables des peines encourues)