# DockerTP

#But de l'application : Créer un container à parti de Tomcat (tomcat:8-jre8) et un autre à partir de Postgres (postgres:9.5) à l'aide de deux Dockerfile (Tomcat étant le serveur et Postgres la base de données), pour ensuite les lier pour avoir une base de données permanente sur l'application web donnée.

#Récupération du dossier de l'application web à partir de github (Lauryao). Création du premier Dockerfile à partir de Tomcat (tomcat:8-jre8). 
#Pour l'afficher sur mon navigateur internet, j'utilise la ligne COPY ./dbproject.war /usr/local/tomcat/webapps dans le Dockerfile (on copie le projet dans le webapps de tomcat, car c'est à partir d'ici que je pourrai avoir accès à l'application web).

#Lier ensuite ces deux containers à l'aide 

#Pour avoir accès à la base de données de façon permanente (qu'elle ne soit pas supprimée à chaque fois qu'on la relance), j'ai ajouté une ligne de commande dans le Dockerfile de Postgres : 
