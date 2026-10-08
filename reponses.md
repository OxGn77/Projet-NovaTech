Identifiant du premier commit : 2a410b9
Commit correpsondant à l'ajout de la page contact : 95e8c80 "Ajout de la page contact"
Il y a eu à ce point 10 commit sur ce projet 
J'ai utilisé la commande suivante : git log --oneline --graph --all

Je vais analyser le deuxièle commit de la fonction contact. Sur ce dernier nous étions dors et déjà sur la bonne branch; il fallait donc simple déclarer le commit et push (git commit -m "Changement contact", puis git push)

Commande choisie :git reset -- mixed HEAD~1` 
Le mode mixed annule l'enregistrement du commit mais gardeles modifications apportées dans les fichiers du dossier de travail (Working Directory).
git reset --hard HEAD~1 aurait supprimé à la fois le commit et toutes les modifications non enregistrées.

On a utilisé git revert HEAD au lieu d'un git reset. Le reset réécrit l'historique en supprimant un commit, ce qui pose problème sur un dépôt distant/partagé. git revert crée un nouveau commit qui annule les modifications du commit ciblé sans altérer l'historique passé.

1) Zone de travail / Zone de staging / Historique :

Zone de travail (Working Directory) : Représente les fichiers réels modifiés sur le disque en local.

Zone de staging (Index) : Zone intermédiaire où l'on prépare avec git add les modifications précises qui feront partie du prochain commit.

Historique (Dépôt local) : Ensemble des commits enregistrés définitivement dans la base de données Git via git commit, que tout les collaborateurs d'un projet verront.

2) Cela permet d'isoler le développement et les tests d'une nouvelle option sans risquer de casser la branche principale (main) qui doit toujours rester stable et fonctionnelle.

3) Dans la Mission 8 (git reset), le commit est supprimé et l'historique est réécrit.
    Dans la Mission 9 (git revert), l'historique est préservé : on ajoute un nouveau commit "inverse" pour conserver la traçabilité complète sur un projet collaboratif.


4) C'est utile quand on a un travail en cours non terminé (qu'on ne veut pas commiter dans un état cassé) et qu'on doit changer d'urgence de branche pour corriger un bug ou traiter une tâche prioritaire.

5) Cherry-pick permet de piquer un commit spécifique au sein d'une branche de dev/test sans embarquer avec lui tout le reste des modifications inachevées de cette branche.


6) HEAD correspond au commit ou la branche sur lequel on se trouve actuellement dans le répertoire de travail.


7) On cherche à revenir en arrière de 2 commit par rapport à l'actuel. 

8) Un tag permet de marquer un point précis dans l'historique en lui attribuant un nom lisible (ex. v1.0.0), très utilisé pour identifier les livraisons ou les versions stables publiées. Cela permet donc de bien vérifier le suivie du projet global. 

9) Ils rendent l'historique lisible, facilitent la revue de code, simplifient la résolution de conflits et permettent d'annuler ou de récupérer (cherry-pick) une modif sans impacter le reste du projet.


10) Certains fichiers ne doivent pas être suivis car ils contiennent des identifiants/clés de sécurité (.env), sont générés automatiquement (cache/, dossiers de build) ou sont propres à la machine locale/environnement de dev (debug.log).
