# OCR---Projet-7

Projet 7 du parcours développeur d'application JAVA d'OpenClassRooms.

Dans ce projet, il est demandé de développer une API web (en REST ou SOAP), une application web et un batch pour les bibliothèques d'une grande ville.

### Résumé du cahier des charges

* Fonctionnalités attendues :
  * Recherche d'ouvrages
  * Visiualisation des exemplaires disponibles
  * Suivi des prêts
  * Prolongation de la période de prêt
  * Envoi automatique de mail quotidien pour les emprunts ayant dépassé la date de fin du prêt
  * Implémentation dès cette 1ère release de création et retour de prêt (ne seront utilisé que par le logiciel du personnel à la release 2.0)
  
* Choix techniques imposés:
  * API web en REST ou SOAP (consommée par application web et batch)
  * Application web avec framework MVC
  * Packaging Maven
  * API web communique avec la base de données
  

### Déploiement des différents services en local :

Avant tout, il est nécessaire d'avoir une version de JDK 11 minimum sur votre machine. Pour l'installer, vous pouvez vous rendre par exemple sur l'un des sites suivant: https://adoptopenjdk.net/  ,  https://www.oracle.com/java/technologies/javase-jdk11-downloads.html ,  https://openjdk.java.net/
    
Ensuite , installer Apache Maven : https://maven.apache.org/

Pour ce projet, j'ai utilisé des bases de données PostgréSQL : https://www.postgresql.org/

Une fois ces différents éléments installés, référez vous à la documentation postgreSQL pour la création des bases de données, j'en ai utilisé 3 afin de séparer :
  * les rapports du traitement automatisé de l'envoi de mail par l'application expired-loan-batch
  * le catalogue de la bibliotheque
  * la gestion des prêts
  
Dans le fichier application.properties (src>main>resources>application.properties), des REST api (ocr_bibliotheque et ocr_loan_api) ainsi que celui de l'application batch, il vous faudra renseigner le nom et mot de passe de l'utilisateur avec lequel vous avez créé vos bases de données (ocr_admin dans mes fichiers comme nom et mot de passe pour l'exemple)

Pour pouvoir tester les 2 REST API(ocr_bibliotheque et ocr_loan_api) et les 2 applications (expired-loan-batch et ocr_webapp) vous trouverez dans chacun de leur dossier des scripts sql de création des tables et un de jeu de données de démonstration.

N'oubliez pas de démarrer vos bases de données.

Pour chacun des fichiers du projet, ouvrez un terminal à la racine du de leur dossier et lancer la commande `mvn spring-boot:run` 

Vous pouvez maintenant vous rendre à l'adresse  `localhost:9091` afin de voir ces différentes applications en action.

### Déploiement sur serveur :

Pour un déploiement sur serveur, je vous conseille de créer un jar via la commande `mvn clean package` à la base des dossiers de 2 REST API(ocr_bibliotheque et ocr_loan_api) et les 2 applications (expired-loan-batch et ocr_webapp), puis de vous reporter à la documentation de votre serveur pour y déployer ces jar et les bases de données.
