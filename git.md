# Git

## Pense bête 

* Afficher les informations du projet
```sh
git status
git diff
git diff --staged
git log
```

* Lister la configuration
```sh
git config --list
git config -l
```

* Pousser une modification
```sh
git add *
git commit -m "Message du commit"
git push
```

* Ajouter des fichiers oubliés
```sh
git commit -m 'Initial commit'
git add forgotten_file
git commit --amend
```

* Supprimer les modifications pour pull la dernière version du repo
```sh
git fetch --all
git reset --hard origin/master
git pull origin master
```

## Configurer le user

```sh
git config --global user.name "bbuzens"
git config --global user.email benoit.buzens@gmail.com
```


## Configurer le remote

* Créer un repo sur Github

* Afficher le(s) repository(ies) distant
```sh
git remote
```

* Ajouter/Modifier le remote dans la configuration locale
```sh
git remote add origin https://github.com/bbuzens/notes
git remote set-url https://github.com/bbuzens/notes
```


## Initialiser un repo

```sh
git init
git add *
git add LICENSE
git commit -m 'Initial project version'
```

## Cloner un repo

```sh
git clone https://github.com/libgit2/libgit2
```
