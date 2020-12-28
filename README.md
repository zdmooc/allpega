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

/var/lib/postgresql/11/main# ls
base          pg_dynshmem   pg_notify    pg_snapshots  pg_subtrans  PG_VERSION  postgresql.auto.conf
global        pg_logical    pg_replslot  pg_stat       pg_tblspc    pg_wal      postmaster.opts
pg_commit_ts  pg_multixact  pg_serial    pg_stat_tmp   pg_twophase  pg_xact     postmaster.pid




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






/var/lib/postgresql/11/main# ps auxf | grep postgres
root       22161  0.0  0.0  17664   816 pts/0    S+   21:47   0:00  |   |           \_ grep --color=auto postgres
postgres   14934  0.0  0.3 228496 29324 ?        Ss   déc.26   0:00 /usr/lib/postgresql/13/bin/postgres -D /var/lib/postgresql/13/main -c config_file=/etc/postgresql/13/main/postgresql.conf
postgres   14938  0.0  0.0 228600  5800 ?        Ss   déc.26   0:00  \_ postgres: 13/main: checkpointer 
postgres   14939  0.0  0.0 228496  5660 ?        Ss   déc.26   0:00  \_ postgres: 13/main: background writer 
postgres   14940  0.0  0.1 228496  9952 ?        Ss   déc.26   0:00  \_ postgres: 13/main: walwriter 
postgres   14941  0.0  0.0 229032  6912 ?        Ss   déc.26   0:00  \_ postgres: 13/main: autovacuum launcher 
postgres   14942  0.0  0.0  82860  4804 ?        Ss   déc.26   0:00  \_ postgres: 13/main: stats collector 
postgres   14943  0.0  0.0 229056  6732 ?        Ss   déc.26   0:00  \_ postgres: 13/main: logical replication launcher 
postgres   14935  0.0  0.3 228404 28964 ?        Ss   déc.26   0:00 /usr/lib/postgresql/12/bin/postgres -D /var/lib/postgresql/12/main -c config_file=/etc/postgresql/12/main/postgresql.conf
postgres   14944  0.0  0.0 228508  6272 ?        Ss   déc.26   0:00  \_ postgres: 12/main: checkpointer   
postgres   14945  0.0  0.0 228404  5828 ?        Ss   déc.26   0:00  \_ postgres: 12/main: background writer   
postgres   14946  0.0  0.1 228404  9956 ?        Ss   déc.26   0:00  \_ postgres: 12/main: walwriter   
postgres   14947  0.0  0.0 228948  6928 ?        Ss   déc.26   0:00  \_ postgres: 12/main: autovacuum launcher   
postgres   14948  0.0  0.0  82784  4688 ?        Ss   déc.26   0:00  \_ postgres: 12/main: stats collector   
postgres   14949  0.0  0.0 228944  6808 ?        Ss   déc.26   0:00  \_ postgres: 12/main: logical replication launcher   
postgres   16206  0.0  0.3 227904 29056 ?        S    déc.26   0:00 /usr/lib/postgresql/11/bin/postgres -D /var/lib/postgresql/11/main -c config_file=/etc/postgresql/11/main/postgresql.conf
postgres   16208  0.0  0.0 228008  6152 ?        Ss   déc.26   0:00  \_ postgres: 11/main: checkpointer   
postgres   16209  0.0  0.0 227904  6112 ?        Ss   déc.26   0:00  \_ postgres: 11/main: background writer   
postgres   16210  0.0  0.1 227904  9904 ?        Ss   déc.26   0:00  \_ postgres: 11/main: walwriter   
postgres   16211  0.0  0.0 228312  6744 ?        Ss   déc.26   0:00  \_ postgres: 11/main: autovacuum launcher   
postgres   16212  0.0  0.0  82820  4428 ?        Ss   déc.26   0:00  \_ postgres: 11/main: stats collector   
postgres   16213  0.0  0.0 228308  6800 ?        Ss   déc.26   0:00  \_ postgres: 11/main: logical replication launcher   
postgres   17561  0.0  0.3 223620 27660 ?        S    déc.26   0:00 /usr/lib/postgresql/9.6/bin/postgres -D /var/lib/postgresql/9.6/main -c config_file=/etc/postgresql/9.6/main/postgresql.conf
postgres   17563  0.0  0.0 223620  4136 ?        Ss   déc.26   0:00  \_ postgres: 9.6/main: checkpointer process   
postgres   17564  0.0  0.0 223620  4136 ?        Ss   déc.26   0:00  \_ postgres: 9.6/main: writer process   
postgres   17565  0.0  0.0 223620  4136 ?        Ss   déc.26   0:00  \_ postgres: 9.6/main: wal writer process   
postgres   17566  0.0  0.0 224024  7232 ?        Ss   déc.26   0:00  \_ postgres: 9.6/main: autovacuum launcher process   
postgres   17567  0.0  0.0  78612  4392 ?        Ss   déc.26   0:00  \_ postgres: 9.6/main: stats collector process   



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

