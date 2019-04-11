# sowboy-free-sf-php-docker-stack
Un stack docker optimal pour multi-projets php7 et Symfony .
Clonez le repo, lancez `docker-compose build` puis `docker-compose up -d` . Tous vos projets sont à placer dans le dossier `symfony` qui sera généré dans le dossier `sowboy-free-sf-php-docker-stack` .
Faites un `docker exec -it sowboy_apps bash` pour entrer dans le container où vous pouvez créer des projets symfony ou gérér des existants .
Un exemple de vhots existe dans le stack (régarder dans le fichier `docker-compose.yml`)
