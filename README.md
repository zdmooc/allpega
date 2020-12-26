# allpega

postgres pour ubuntu
https://www.postgresql.org/download/linux/ubuntu/


service postgresql status
service postgresql stop
service postgresql start
service postgresql reload


* configuration : /etc/postgresql/
total 32
drwxr-xr-x   6 postgres postgres  4096 déc.  26 20:36 .
drwxr-xr-x 144 root     root     12288 déc.  26 11:24 ..
drwxr-xr-x   3 postgres postgres  4096 déc.  26 20:29 11
drwxr-xr-x   3 postgres postgres  4096 déc.  26 11:30 12
drwxr-xr-x   3 postgres postgres  4096 déc.  26 11:24 13
drwxr-xr-x   3 postgres postgres  4096 déc.  26 20:36 9.6



* datas : /var/lib/postgresql/


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
