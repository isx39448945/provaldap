# provaldap:2019
## ASIX M06-ASO @isx39448945 Curs 2019-2020

### Servidor ldap adri.cat

docker hub: https://hub.docker.com/repository/docker/adrinarvaez/provaldap  
github: https://github.com/isx39448945/provaldap

### Exemples d'execució del container

***Interactive***  
docker run --rm --name provaldap -h provaldap -it adrinarvaez/provaldap:2019 /bin/bash  
bash install.sh  
/sbin/slapd

***Detach***  
docker run --rm --name provaldap -h provaldap -d adrinarvaez/provaldap:2019

### Exemple de confirmació de l'estat de la base de dades

***Dins del container***  
ldapsearch -x -LLL -h provaldap -b 'dc=adri,dc=cat'

***Des de fòra del container***  
ldapsearch -x -LLL -h 172.17.0.2 -b 'dc=adri,dc=cat' (el host pot variar segons la configuració de la xarxa docker)

### Procés de la creació del servidor ldap adri.cat

+ Copiem els fitxers necessàris de qualssevol base de dades ldap i els configurem adientment. (DB CONF, slapd.conf, ldap.conf)
+ Elaborem els fitxer que automatitzaran la tasca de crear el nostre servidor ldap. (Dockerfile, install.sh, startup.sh)
+ Creem els fitxers schema que ens demanen per crear els objectClass indepeOrgPerson i marchenaAccount. (indepe.schema, marchena.schema)
+ Creem els fitxers d'addició de dades. (adri.ldif, marchena.ldif)
+ Finalment, comprovem l'estat del servidor fent ús de qualssevol comanda ldap que ens verifiqui un funcionament correcte del mateix. (ldapsearch)
