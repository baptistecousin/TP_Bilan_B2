# TP_Bilan_B2
TP ou l'on installe Docker avec un script d'installation automatique. Puis installation avec Docker d'un Zabbix et de Wordpress.

# Il est possible de consulter le PDF "Explications" join dans le repository afin d'avoir plus de details et des images


## Installation de Docker à l'aide du script.sh
Nous allons utiliser le script que nous avons crée (installation_docker.sh) afin d’installer Docker automatiquement.
[Exectution du Script]
Une fois l’installation terminée, on peut exécuter : docker run hello-world , afin de vérifier le bon fonctionnement.
Pour nous, ça fonctionne on peut donc continuer.

## Installation de Zabbix
Une fois docker installé à l’aide de notre script, on crée un dossier /opt/zabbix, puis 

cd /opt/zabbix

on récupère les fichiers Zabbix officiels avec les commandes :

cd /opt
sudo git clone https://github.com/zabbix/zabbix-docker.git
cd zabbix-docker
sudo chown -R "$USER":"$USER" .

On peut écrire ensuite le fichier docker-compose yaml ou comme nous, choisir un fichier déjà ecrit en tapant ces commandes :

ls docker-compose_v3_* → liste les fichiers yml disponibles

cp docker-compose_v3_ubuntu_mysql_latest.yaml docker-compose.yml → utilise celui de la dernière version ubuntu (compatible debian) avec mysql. En le copiant et en le nommant docker-compose.yml


(Mon fichier docker-compose.yml est disponile sur git dans le dossier /zabbix/docker-compose.yml)


On fait un nano docker-compose.yml pour modifier les mots de passe, le nom d’hôte du zabbix etc…
Nous les laisserons par défaut pour le TP.

On démarre ensuite l’installation de Zabbix via Docker compose avec la commande
Docker compose up -d
2 à 3 minutes plus tard, Zabbix est installé et on peut y accéder avec l’adresse 192.168.20.34 :8080.


## Installation de WordPress
Pour installer Wordpress on procède de la même façon, on crée un dossier dans /opt/wordpress, on y crée le fichier docker-compose.yml.

(Le fichier est également disponible, cette fois-ci dans le dossier /wp/docker-compose.yml)

Une fois ce fichier crée, on lance l’installation avec la commande : docker compose up -d
L’installation se lance.

Une fois l’installation terminée, en moins de 5 minutes, on se rend sur la page web à l’adresse 192.168.20.34 :8081. On a attribué le port 8081 afin de ne pas avoir de conflit avec Zabbix qui est sur le port par défaut, 8080.

Wordpress fonctionne bien pour nous.


## Note sur les fichiers yml :
Les fichiers yml contiennent tous les paramètres d’une installation, on peut y ajouter ce que l’on veut afin de personnaliser notre installation et remonter un service en moins de 5 minutes, en cas de panne.


## Envoi des fichiers vers GitHub :
Pour envoyer les fichiers vers Github, nous allons utiliser Git. S’il n’est pas installé, l’installer en faisant apt update && apt install git -y
J’ai placé mes fichiers dans un dossier /pour_git /.
Je renomme ma branche principale en « main » avec la commande : git branch -M main
Ensuite, je fais un git remote add origin https://github.com/baptistecousin/TP_Bilan_B2
Je fast un git pull afin de récupérer le readme.md crée directement depuis github. Ensuite, on fait un git add . afin d’ajouter tous les fichiers.
Puis un premier git commit et enfin un git push.