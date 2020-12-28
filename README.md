# allpega

postgres pour ubuntu
https://www.postgresql.org/download/linux/ubuntu/

apt-cache search postgres
sudo -s

service postgresql status
service postgresql stop
service postgresql start
service postgresql reload


* configuration : /etc/postgresql/

etc/postgresql/11/main# ls -la
total 60
drwxr-xr-x 3 postgres postgres  4096 déc.  26 20:29 .
drwxr-xr-x 3 postgres postgres  4096 déc.  26 20:29 ..
drwxr-xr-x 2 postgres postgres  4096 déc.  26 20:29 conf.d
-rw-r--r-- 1 postgres postgres   315 déc.  26 20:29 environment
-rw-r--r-- 1 postgres postgres   143 déc.  26 20:29 pg_ctl.conf
-rw-r----- 1 postgres postgres  4686 déc.  26 20:29 pg_hba.conf
-rw-r----- 1 postgres postgres  1636 déc.  26 20:29 pg_ident.conf
-rw-r--r-- 1 postgres postgres 24295 déc.  26 20:29 postgresql.conf
-rw-r--r-- 1 postgres postgres   317 déc.  26 20:29 start.conf



* datas : /var/lib/postgresql/

usr/lib/postgresql/11/bin# ls
clusterdb   dropuser           pg_basebackup   pg_ctl      pg_receivewal   pg_rewind       pg_upgrade           postmaster  vacuumlo
createdb    initdb             pgbench         pg_dump     pg_recvlogical  pg_standby      pg_verify_checksums  psql
createuser  oid2name           pg_config       pg_dumpall  pg_resetwal     pg_test_fsync   pg_waldump           reindexdb
dropdb      pg_archivecleanup  pg_controldata  pg_isready  pg_restore      pg_test_timing  postgres             vacuumdb


* binaire principal : /usr/lib/postgresql/XX/bin/postgres

/usr/lib/postgresql/XX/bin$ ls
clusterdb   dropuser           pg_basebackup   pg_ctl      pg_receivewal   pg_rewind       pg_upgrade           postmaster  vacuumlo
createdb    initdb             pgbench         pg_dump     pg_recvlogical  pg_standby      pg_verify_checksums  psql
createuser  oid2name           pg_config       pg_dumpall  pg_resetwal     pg_test_fsync   pg_waldump           reindexdb
dropdb      pg_archivecleanup  pg_controldata  pg_isready  pg_restore      pg_test_timing  postgres             vacuumdb


* binaires pg : /usr/bin/ (pg_*)
/usr/bin$ ls pg_*
pg_archivecleanup  pg_config         pg_ctlcluster   pg_dumpall     pg_receivewal   pg_renamecluster   pg_virtualenv
pg_basebackup      pg_conftool       pg_dropcluster  pg_isready     pg_receivexlog  pg_restore
pg_buildext        pg_createcluster  pg_dump         pg_lsclusters  pg_recvlogical  pg_upgradecluster



author xavki

xavki

Postgresql : binaires
 
* pg_ctl :
	- gestion de l'instance/cluster
	- start/stop/kill
	- init: création autre espace de datas
	- promote : promotion du standby

* psql :
	- client de connexion à un cluster
	- précision utilisateur et/ou db
	- passage de sql en cli ou script sql


Spécifique Debian

* pg_createcluster :
	- création d'un cluster (une instance PG)
	-	création des répertoires (/etc /var/lib/)

* pg_dropcluster :
	- suppression d'un cluster
	- cluster arrêté

* pg_lscluster :
	- lister les cluster

* pg_ctlcluster :
	- équivalent du pg_ctl
	- contrôle du cluster (stop/start...)


Spécifiques Sauvegardes

* pg_dump:
	- sauvegarde d'une instance
	- différents formats : plain text, binaire...
	- différents niveaux d'objets (cluster/db/table/schéma)

* pg_dumpall:
	- sauvegarde intégrale en format binaire

* pg_restore:
	- restauration à partir d'une sauvegarde (pg_dumpall)


Wrappers

équivalent de commandes sql


* createdb :
	- création d'une base de données

* dropdb :
	- suppression d'une base de données

* createuser :
	- création d'un utilisateur

* dropuser :
	- suppression d'un user


Maintenance

* reindexdb :
	- réindexation des index avec des paramètres pour restreindre le périmètre

* vacuumdb :
	- tâche de maintenance (ménage)

* vacuumlo :
	- suppression de large objects


Spécifiques système avancées

* pg_controldata : 
	- vérifie l'état du serveur et des infos critiques

* pg_resetwal : 
	- en cas de crash avec pb de  WAL (Write Ahead Logging) 
	- attention : datas inconsistentes (dernier recours)

* pg_receive_wal :
	- récupération des WAL d'une autre DB

* pg_basebackup:
	- récupération de datas par une connexion à une autre DB (ex : init réplication)

