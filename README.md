# Explorez mon code source !

## Une seule vision : mêler l'utile à la pédagogie

Pas facile de trouver des ressources en Français pour apprendre le développement web n'est-ce pas ? Pas facile non plus de trouver un projet *concret* avec du code source rédigé en Français et des commentaires clairs...

**Ce site est là pour combler ce manque.**

J'ai commencé par lister les développeurs web Français sur YouTube. Je vais enrichir le contenu petit à petit grâce à vos contributions : podcasts, sites web, formations, conférences, livres, écoles etc.

J'ai profité de la création de ce site pour en faire un projet pédagogique open source. J'ai pris le temps de le faire au mieux et de commenter un maximum de choses pour faciliter la lecture de son code source et surtout pour que vous puissiez apprendre d'un projet bien réel et en production !

## Apprendre les bases : HTML/CSS/JavaScript

Le but ici est d'apprendre les bases de la programmation web et de démontrer que même avec les bases, on peut déjà faire des sites évolués.

Vous ne trouverez donc **pas** de frameworks ni d'outils spécifiques (préprocesseurs CSS par exemple) pour réaliser ce site, juste du pur HTML5/CSS3/JavaScript (ES6) codé *à la main à l'ancienne<sup>TM</sup>*.

C'est un choix délibéré de ma part pour montrer qu'on n'a pas besoin de tous ces frameworks / outils pour créer des projets utiles et intéressants.

## 🇫🇷 Code source et commentaires en Français (cocorico 🐓)

Pour éviter de laisser de côté une partie de la population qui ne parle pas Anglais, j'ai fait le choix de rédiger tout ce que j'ai pu en Français : noms de variables et de fonctions, commentaires, noms de fichiers...

Vous trouverez également des explications techniques sur les choix que j'ai fait pour réaliser ce site.

Les fichiers HTML, CSS et JavaScript sont tous commentés, pensez à lire leur contenu !

Le code source n'est pas minifié/compressé/uglifié, il est lisible, directement sur le site web <i>comme au bon vieux temps<sup>TM</sup> !</i> Je préfère troquer quelques kilo-octets sur le réseau contre un site intégralement ouvert et modifiable par un débutant pour s'en approprier le contenu et le code.

> Je vous invite donc vivement à abuser du clic droit -> Afficher le code source (ou Inspecter). Regardez, manipulez, modifiez, bidouillez, c'est comme ça qu'on apprend, alors faites-vous plaisir !

## Un dépôt GitHub propre et honnête

J'ai essayé de commiter souvent mon code source pour que vous puissiez voir l'évolution du site internet : comment j'ai créé petit à petit les fonctionnalités. 

C'est une bonne pratique de commiter de façon *atomique* chaque changement. Ça permet de faciliter l'isolation des bogues et de bien séparer les modifications les unes des autres pour faire un `git bisect` par exemple et trouver le commit coupable !

Je n'ai pas essayé d'effacer mes erreurs, car il est important de comprendre que même les professionnels font des erreurs. Trop souvent les débutants pensent qu'on développe "en une fois" un morceau de code et du premier coup, ce qui est totalement faux. On procède petit à petit, par itérations successives.

> N'hésitez donc pas à naviguer dans l'historique du dépôt GitHub pour voir mes différents commits.

## Clé secrète pour l'API YouTube

Si vous téléchargez le site chez vous, et que vous souhaitez générer le fichier `donnees.json` vous rencontrerez cette erreur :

```
Clé d'authentification introuvable pour se connecter à l'API YouTube. Il n'y a pas de fichier cle_api.txt ni de variable d'environnement 'CLE_API'.
```

C'est parfaitement normal.

Je n'ai pas mis ma clé secrète d'accès à l'API YouTube dans le dépôt pour des raisons évidentes.

Par conséquent, vous devrez [créer votre propre clé API](https://developers.google.com/youtube/registering_an_application) et la mettre à la racine du dépôt dans un fichier nommé `cle_api.txt` pour pouvoir appeler l'API YouTube et générer le fichier de données.

## Architecture du projet et choix techniques

Le projet est composé d'un fichier `index.html` qui contient le contenu statique du site internet (tout sauf la liste des développeurs web).

Un script nommé `generer-donnees-enrichies.js` contenu dans le sous-dossier `js` est exécuté par NodeJS au moment de la construction du site (*build*).

Un fichier `TODO` a la racine du projet indique les prochaines fonctionnalités sur lesquelles je dois travailler.

## Comment télécharger et lancer ce site chez vous ?

> N'hésitez pas à me contacter pour que je clarifie cette procédure si besoin.

1. Cloner ce dépôt Git dans VSCode et installez l'extension Live Server : pour ça lisez les [instructions suivantes](https://github.com/javascriptdezero/module-debutant/tree/master/cours#En-savoir-plus-sur-les-exercices) en remplaçant à l'étape 5.iii le dépôt GitHub mentionné par celui-ci : https://github.com/javascriptdezero/ressources-dev-web.git. Ouvrez le dépôt.
2. Depuis VSCode, ouvrez un terminal depuis le menu Terminal > Nouveau Terminal.
3. Dans le terminal, tapez `npm install` puis validez avec ENTREE. Il devrait afficher quelque chose comme ça :
```
iMac:ressources-dev-web jeremy$ npm install
added 35 packages from 40 contributors and audited 221 packages in 1.293s
found 0 vulnerabilities
```
4. Créez la clé API pour accéder à YouTube comme indiqué à [cette section](#Cle-secrete-pour-l-API-YouTube). Une clé API ressemble à ceci : `AIzaSyC_GXKx3W_v1VvhT13BMz-AfquRYZP9ees`
5. Depuis VSCode créez un nouveau fichier `cle_api.txt` à la racine du dossier.
6. Collez votre clé API dans ce fichier et sauvegardez.
7. Lancez le script de construction de l'application (*build*) : depuis le terminal, tapez `npm run build` puis validez avec ENTREE. Il devrait afficher quelque chose comme ça :
```
iMac:ressources-dev-web jeremy$ npm run build

> ledevweb.fr@1.0.0 build /Users/jeremy/Desktop/ressources-dev-web
> echo 'Création du fichier donnees.json...' && node js/generer-donnees-enrichies.js && echo 'Terminé.'

Création du fichier donnees.json...
Clé d'authentification trouvée depuis le fichier 'cle_api.txt'.
Terminé.
```
8. Le script de construction a généré un fichier `donnees.json` situé dans le sous-dossier `json`.
9. Vous pouvez lancer le site internet grâce à l'extension Live Server que vous avez dû installer à l'étape 1 en cliquant sur "Go Live" dans la barre bleue en bas de VSCode.
10. Le site va se charger dans votre navigateur et la liste devrait apparaître.

## Mise en ligne : Netlify

J'ai utilisé pour la première fois le service [Netlify](www.netlify.com) pour mettre en ligne ce site internet.

Malheureusement il n'existe pas de solution équivalente en Français à ma connaissance.

Je vais donc être bref.

Ce service permet de publier automatiquement votre site internet sur le domaine de votre choix. Ici le nom de domaine est www.ledevweb.fr.

La publication s'effectue à chaque fois que vous poussez votre branche sur votre dépôt GitHub qui héberge le code source du site.

C'est très pratique comme fonctionnement et ça évite de passer par un système FTP classique pour envoyer ces données sur le serveur web.

## N'hésitez pas à participer et à partager !

Si vous trouvez un bogue, une faute de frappe ou que vous aimeriez bien plus d'explications sur un bout de code, contactez-moi via Twitter [@JeremyMouzin](https://www.jeremymouzin.com) ou par email sur jeremy@javascriptdezero.com.

Si vous aimez ce projet et que vous voulez le soutenir, merci de partager l'adresse du site à votre entourage ou à votre communauté : <a href="https://twitter.com/intent/tweet?text=D%C3%A9couvrez%20la%20%23liste%20de%20tous%20les%20%23webdev%20Fran%C3%A7ais%20sur%20%23YouTube.%20Parfait%20pour%20apprendre%20le%20d%C3%A9veloppement%20web%20en%20vid%C3%A9o%20!%20https%3A//www.ledevweb.fr%20via%20%40JeremyMouzin">partagez sur Twitter</a>.

Vous pouvez également lui ajouter une étoile en cliquant sur le bouton "⭑Star" en haut à droite.

## Qui suis-je ?

Je m'appelle Jérémy Mouzin, je suis le créateur de la formation [JavaScript de Zéro](https://www.javascriptdezero.com).

J'enseigne la programmation aux débutants complets en utilisant comme premier langage le JavaScript.
