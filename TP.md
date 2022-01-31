Mathieu BOUCHER
Clément DELBARRE
Noé MATTIELLIO
Grégoire DUJARDIN

### Config Jenkins

Le projet a été défini comme "pipeline" sur Jenkins en tant que "pipeline script from SCM" avec comme target le repo Github et comme script le Jenkinsfile présent.

### Config Nexus

Nexus a été configuré en local (port 8081). Un nouveau repository de type maven2 (hosted) a été créé avec comme politique de version "release".
### Jenkinsfile

Avant de lancer la 1ère étape du Jenkinsfile, Jenkins va récupérer les sources présentes sur le Github sur la branche master.

La 1ère étape du script ("build") exécute la commande "mvn clean package" qui supprimera le dossier /target à chaque build et qui recompilera les sources pour former un package jar.

La 2ème étape ("test") va exécuter les tests maven grâce à la commande "mvn test".

la 3ème étape ("publish") va publier le package sur le serveur Nexus où on pourra y retrouver tous nos packages.
Le script a été généré grâce à l'utilitaire "Snippet Generator" de Jenkins en tant que "nexusArtefactUploader" où les informations du projet ainsi que l'URL du repo Nexus ont été renseignés afin de générer le script correspondant.

Une fois que les étapes sont terminées, l'instruction "post" est appelée systématiquement. En cas de succès de toutes les commandes précédentes, on archive notre package dans le dossier /target
et, même si une commande a échoué, on enregistre le rapport de test jUnit dans Jenkins.