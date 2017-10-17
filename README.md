# DockerTP

# But de l'application : Créer un container à parti de Tomcat (tomcat:8-jre8) et un autre à partir de Postgres (postgres:9.5) à l'aide de deux Dockerfile (Tomcat étant le serveur et Postgres la base de données), pour ensuite les lier pour avoir une base de données permanente sur l'application web donnée.

# Récupération du dossier de l'application web (warrepo) à partir de github (Lauryao).
# Création du premier Dockerfile pour l'image de Tomcat (tomcat:8-jre8). 
# Pour l'afficher sur mon navigateur internet, j'utilise la ligne COPY ./dbproject.war /usr/local/tomcat/webapps dans le Dockerfile (on       copie le projet dans le webapps de tomcat, car c'est à partir d'ici que je pourrai avoir accès à l'application web).
# Docker build -t shoes .  // pour créer l'image à partir du DockerFile, -t pour donner un nom à l'image
# Docker run -d --name myapp -p 8887:8080 shoes  // pour démarrer le container à partir de l'image en lui donnant un nom grâce à --name, en   mappant un port grâce à -p, -d sert à le lancer en tâche de fond, pour ne pas rentrer directement dans le container 
# J'ai bien accès à l'application web à partir de cette adresse 192.168.99.100:8887 (étant donné que je suis sur Docker Toolbox, je ne peux   y accéder en localhost.
# Créaton d'un dossier Postgres pour la mise en place du deuxième Dockerfile pour l'image de Postgres (Postgres:9.5)
# Pour réutiliser la structure de la base de données donnée, j'utilise la ligne COPY ./init-db.sql /docker-entrypoint-initdb.d/
# Pour avoir accès à la base de données de façon permanente (qu'elle ne soit pas supprimée à chaque fois qu'on la relance), j'ai ajouté une ligne de commande dans le Dockerfile de Postgres : VOLUME ["/var/lib/postgresql/data"]



# Lier ensuite ces deux containers à l'aide 

