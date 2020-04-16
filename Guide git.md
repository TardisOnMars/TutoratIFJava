# Guide pour l'utilisation de git (github/gitlab)
## Auteurs
David Hamidovic
Sophie Villenave

## Git, qu'est-ce que c'est ?
Quand on débute la programmation, nos programmes restent simples et personnels. On se contente de les sauvegarder localement sur notre machine et/ou de les sauvegarder sur une clé usb.
Cependant lorsque l'on a besoin de collaborer sur un code commun, lorsque l'on change souvent de machines ou alors que l'on veut garder une trace de nos modifications, on utilise ce qui s'appelle un gestionnaire de version.
Il existe de multiple gestionnaires de version, mais celui qui est sans aucun doute le plus utilisé est git.
Que permet git ? Créer un dépôt en local pour avoir accès aux différentes versions du code. Mettre en ligne ce dépôt pour le sauvegarder dans le cloud et le partager avec des collaborateurs. Et plein d'autres choses (pipeline de test...) que nous n'aborderont pas ici !

## Glossaire
* repository / dépôt :
* commit :
* pull :
* push :
* branch :

## Résumé des bonnes pratiques
* Faire des "commits" régulièrement
* Ecrire des messages de commit utiles et compréhensible (pour soi et les autres).
* Faire des commits atomiques, deux bugs, deux commits.
* Exécuter les tests avant de commit.
* Utiliser le système de branche

## Commandes à connaître 
* Obtenir de l'aide sur l'utilisation de la commande git
```
git help [commande]
```

* Classiquement l'ordre d'exécution des commandes pour commit serait ceci : 
```
git status // Pour regarder ce qui a été changé
git add // Pour ajouter les fichiers que vous souhaitez versionner
git commit -a -m “message” // Pour commit tous les changements en indiquant le message de commit
```

Mettre à jour le dépôt distant avec vos changements
```
git push
```

Récupérer les mises à jour disponibles à distance
```
git pull
```

Pour montrer les différences entre le dernier commit et les fichiers actuels
``` 
git diff
```

Commandes pour les branches
Pour afficher toutes les branches (incluant les distantes)
```
git branch -r
```

Créer une branche localement
```
git checkout -b [branche] 
```

Pousser la nouvelle branche sur le dépôt distant en créant un lien entre la branche locale et distante
	git push -u origin [nouvelleBranche] (à faire une fois)
	git push --set-upstream origin [BrancheRemote] (expression équivalente)
Si vous ne voulez pas push on peut juste créer un lien :
	git branch -u [BrancheRemote]


On peut finalement merge une branche (locale ou distante) dans la branche actuelle :
	git merge [autreBranche]

Pour switch d’une branche à l’autre : 
	git checkout [nomBranche]
Supprimer des branches : 
Vous avez merge votre branche et fini votre travail et vous voulez supprimer vos branches.
Depuis n’importe quelle branche : 
	git push -d origin [nomBranche] (Suppression sur le server)
	git branch -D [nomBranche] (Suppression en local)
Conflit lors d’un merge
Occasionnellement (?) un conflit peut arriver lors d’un merge. On peut tout d’abord annuler le merge avec : 
	git merge --abort

Lors du conflit on peut voir ou il y’a eu conflit en faisant :
	git status

Git est sympa et va, dans chaque fichier, indiquer où sont les conflits


HEAD correspond à la branche actuelle, “aaaa” est le nom de ma branche que je voulais merge. le ======= sépare les deux.
Il suffit de modifier le fichier, d’ajouter les changements dans la staging area (git commit add .) et de commit.

Des outils existent pour résoudre ces conflits comme p4merge (mais la flemme d’apprendre maintenant).

Revert un commit
Pour ça il faut d’abord afficher l’historique des commits : 
	git log 


On récupère l’ID du commit (checksum) et on exécute la commande suivante : 
	git revert [checksum]
Git revert un seul commit, que ce soit le dernier ou le préantépénultième, c’est le commit lié au checksum passé en paramètre.

Pour revert le dernier commit on peut faire :
	git revert HEAD (revert le dernier commit)

Pour revert les n derniers commits : 
	git revert HEAD~n..  (revert les n derniers commits)
git revert [idCommit]..  (revert tous les commits jusqu’au commit entre crochet (exclu))

Supprimer tous les changements (définitif)
Pour supprimer les changements non commit, il suffit de faire :
	git reset --hard (dangereux, définitif)*

Git blame
rdv ici


Le dico
git config 
Permet de configurer le nom et l’adresse mail (et autres joyeusetés)
	git config --global user.name “[nom]”
	git config --global user.email “[email@caramail.com]”
git init
Permet d’initialiser le dépôt
	git init [nom]
git clone
Permet de cloner à partir d’un URL un dépôt
	git clone [URL]

git status
Permet de voir les fichiers modifiés (not staged for commit), les nouveaux fichiers (untracked files)
	git status
git add
Permet d’ajouter un fichier modifié ou un nouveau fichier dans la staging area (nécessaire pour commit)
	git add [nom] (pour un fichier)
	git add . (tous les fichiers)
git commit
Permet de commit tous les changements dans la staging area. Cela crée un snapshot (une nouvelle version du programme qu’on pourra retrouver ultérieurement)
	git commit (ouvre un éditeur de texte pour ajouter un message (relou))
	git commit -m “message” (permet de rajouter un message directement depuis la 
ligne de commande)
git diff
Permet de voir la différence entre l’état actuel du dépôt et le dernier commit
	git diff
	git diff [branch1] [branch2] (pour comparer 2 branches, même les remote
branches)
git reset
Permet d’enlever un fichier de la staging area.
	git reset [nom]
git rm
Permet de supprimer un dossier, git en prend compte directement.
	git rm [nom]
git log
Permet de voir l’historique de la branche actuel, avec le checksum (ID) de chaque commit permettant de revenir sur un ancien commit 
	git log
git show
Permet de montrer les métadonnées et les diff d’un commit 
	git show [commit ID]
git branch
Permet de montrer les branches existantes.
	git branch
	git branch -r (montre aussi les remotes)
	git branch -D [nomBranche] (supprime la branche locale)
git checkout
Permet changer d’une branche à l’autre.
	git checkout [nomBranche]
	git checkout -b [nomBranche] (créé une branche et change de branche)
	git checkout -b [nomBranche] [brancheOriginale] (brancheOriginale peut être 
distante)
git merge
Permet de merge 2 branches
	git merge [brancheAMerge] (merge brancheAMerge dans la branche actuelle)
	git merge --abort (annule le merge courant)
git push
Permet de mettre à jour le travail sur le dépôt distant.
	git push origin [brancheLocal]
	git push (si la branche local est lié à la branche distante)
	git push --set-upstream origin [brancheLocale] (pour créer un lien)
	git push -d origin [nomBranche] (supprime la branche sur le server)

git pull
Permet de récupérer les fichiers du dépôt distant.
	git pull
git revert
Permet de revert un ou plusieurs commits
	git revert [checksum] (revert le commit ayant l’ID checksum)
git revert HEAD (revert le dernier commit)
	git revert HEAD~n..  (revert les n derniers commits)
git revert [idCommit]..  (revert tous les commits jusqu’au commit entre crochet, le commit idCommit est exclu)


git blame
Pour voir qui à modifier en dernier un fichier ligne par ligne. (à utiliser avec parcimonie)
	git blame [fichier]


