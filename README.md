# DockerTP

# But de l'application : Créer un container à parti de Tomcat (tomcat:8-jre8) et un autre à partir de Postgres (postgres:9.5) à l'aide de deux Dockerfile (Tomcat étant le serveur et Postgres la base de données), pour ensuite les lier pour avoir une base de données permanente sur l'application web donnée.

Récupération du dossier de l'application web (warrepo) à partir de github (Lauryao).
Création du premier Dockerfile pour l'image de Tomcat (tomcat:8-jre8). 
Pour l'afficher sur mon navigateur internet, j'utilise la ligne COPY ./dbproject.war /usr/local/tomcat/webapps dans le Dockerfile (on       copie le projet dans le webapps de tomcat, car c'est à partir d'ici que je pourrai avoir accès à l'application web).
Docker build -t shoes .  // pour créer l'image à partir du DockerFile, -t pour donner un nom à l'image
J'ai bien accès à l'application web à partir de cette adresse 192.168.99.100:8887 (étant donné que je suis sur Docker Toolbox, je ne peux   y accéder en localhost.
Créaton d'un dossier Postgres pour la mise en place du deuxième Dockerfile pour l'image de Postgres (Postgres:9.5)
Pour réutiliser la structure de la base de données donnée, j'utilise la ligne COPY ./init-db.sql /docker-entrypoint-initdb.d/
Pour avoir accès à la base de données de façon permanente (qu'elle ne soit pas supprimée à chaque fois qu'on stop et start la base de données), j'ai ajouté une ligne de commande dans le Dockerfile de Postgres : VOLUME ["/var/lib/postgresql/data"]
Docker build -t dbimage .   // pour créer l'image à partir du Dockerfile, -t pour donner un nom à l'image
Docker run -d --name db dbimage  // pour démarrer le container à partir de l'image en lui donnant un nom grâce a --name 
Docker run -d --name myapp -p 8887:8080 --link db shoes   // -d pour le démarrer en arrière fond, --name pour le nom, -p pour le port et --link sert à lier deux containers (celui qu'on créé -> myapp avec celui de la base de données déjà créées -> db à partir de l'image shoes)
L'application lancé, j'ai bien la base de données qui est liée à l'application web, et même en arrêtant puis relançant le container de la base de données, les données déjà enregistrés ne sont pas perdues et sont bien gardées.



