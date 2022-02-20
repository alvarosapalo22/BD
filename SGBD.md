 # **Part I - INSTAL·LACIÓ SGBD MySQL Percona (màx. 6 punts)**

*Primerament, el que farem es descarregar els paquets utilitzant el sudo yum -y Update.*

![image](https://user-images.githubusercontent.com/61474765/154855787-13dd2029-cf98-434f-ad3d-5b2efeb2094b.png)

*Ara, instal·larem el repositori del Percona utilitzant la següent comanda: sudo yum install https://repo.percona.com/yum/percona-release-latest.noarch.rpm
Farem y quan ens ho demani per poder continuar amb la instal·lació.*
![image](https://user-images.githubusercontent.com/61474765/154857029-5a66b5cd-766c-4d2a-bb7e-3db59e6e36ee.png)

*Amb la comanda rpm -qi percona-release podrem confirmar l’instal·lació del repositori del Percona. 
Podem comprovar que esta de moment tot correcte.*

![image](https://user-images.githubusercontent.com/61474765/154857511-144420fa-1a85-450d-a50c-f94b096eef36.png)

*Un cop comprovat, habilitarem el repositori de percona server utilizant la comanda: sudo percona-release setup ps80.*
![image](https://user-images.githubusercontent.com/61474765/154857676-9badde52-98e6-48f3-9123-52968f7862af.png)

*Instal·larem el Percona Server en el nostre servidor fent servir la comanda sudo yum install  percona-server-server. Farem un y quan ens demani si volem continuar amb l’instal·lació.*
![image](https://user-images.githubusercontent.com/61474765/154857765-4b3dcf37-ab44-4244-8f44-089df0292e35.png)

*Comprovarem que s’ha instal·lat correctament el Percona Server amb la comanda: rpm -qi percona-server-server.
Comprovem que a estat correcte*

![image](https://user-images.githubusercontent.com/61474765/154857794-21115b97-b85e-4976-946c-cf790665dc8c.png)

*Ara, iniciarem i configurarem el servei per tal de que s’iniciï al inici sense haver d’estar iniciant-lo cada vegada que arranquem la màquina amb la comanda: sudo systemctl enable –now mysqld.*
![image](https://user-images.githubusercontent.com/61474765/154857809-79e0839b-ac55-4e7c-80aa-8c7d3317c291.png)

*I ara, comprovem que s’ha iniciat correctament amb la comanda sudo systemctl status mysqld.*
![image](https://user-images.githubusercontent.com/61474765/154857826-83b95dfb-5e81-44db-a493-95938732e616.png)


## RESPON O COMPROVA ELS SEGÜENTS APARTATS

***1.	Un cop realitzada la instal·lació realitza una securització de la mateixa. Quin programa realitza aquesta tasca? Realitza una securització de la instal·lació indicant que la contrasenya de root sigui patata.***

Aquesta tasca la realitza el mysql_secure_installation.
Primerament, el que farem es obtenir la nostra contrasenya temporal amb la comanda: sudo grep “temporary password” /var/log/mysqld.log
![image](https://user-images.githubusercontent.com/61474765/154858132-a7cfdbca-092d-4914-8a4a-2e17aae106be.png)

Per tema de les polítiques de les contrasenyes, no podrem posar-la per això primerament haurem de canviar aquesta política.
Entrarem dintre del mysql, amb la comanda mysql -u root -p posant la contrasenya temporal que ens han donat anteriorment.
![image](https://user-images.githubusercontent.com/61474765/154858278-683e48b0-033a-40eb-a188-e79d5a0a9108.png)

Un cop dintre el primer que farem es posar-li 6 com a longitud mínima de la contrasenya amb la comanda SET GLOBAL validate_password.lenght = 6; Un cop feta farem que la política de contrasenya sigui la mínima amb la comanda SET GLOBAL validate_password.policy=LOW; I finalment amb la comanda SHOW VARIABLES LIKE ‘validate_password%’; podem comprovar que a aplicat correctament els canvis.

![image](https://user-images.githubusercontent.com/61474765/154858293-5fd9f2f6-9a4b-4971-ab62-e7dd172ddba7.png)

Ara, amb la comanda ALTER USER ‘root’@’localhost’ IDENTIFIED BY ‘patata’; li canviem la contrasenya a l’usuari root posant-li patata.
![image](https://user-images.githubusercontent.com/61474765/154858316-fea968b6-318e-45d3-bb79-be1d0e593b23.png)

Ara, si entrem a l’arxiu mysql_secure_installation amb la contrasenya patata comprovem que ens entra perfectament.
![image](https://user-images.githubusercontent.com/61474765/154858328-07d19239-0c16-4000-bb3b-78491f923ab1.png)

Ara, per tal de poder connectar-nos amb el Workbench, haurem de obrir el port 3306 que es el que utilitzem per fer la connexió amb les comandes:
sudo Firewall-cmd –zone=public –add-port=3306/tcp –permanent
i 
sudo Firewall-cmd –reload 
![image](https://user-images.githubusercontent.com/61474765/154858346-98232851-1430-4c91-8512-5708dd1897ab.png)

Ara, crearem la connexió amb el Workbench
![image](https://user-images.githubusercontent.com/61474765/154858374-5e29fd46-837a-4661-97b5-ae30457c25dc.png)

***2.	Quines són les instruccions per arrancar / verificar status / apagar servei de la base de dades de Percona Server en el CentOS 7.***

Per arrancar el servei seria utilitzant la comanda sudo systemctl start mysqld.
![image](https://user-images.githubusercontent.com/61474765/154858640-a6c7c498-3542-46ec-b508-46b67481e161.png)

Per verificar el status es utilitzant la comanda sudo systemctl status mysqld.
![image](https://user-images.githubusercontent.com/61474765/154858653-9f74f242-4d31-4a57-9962-a8eb754b764b.png)

I per apagar el servei utilitzaríem la comanda sudo systemctl stop mysqld.
![image](https://user-images.githubusercontent.com/61474765/154858674-fa61034b-8daf-4571-9e92-e478400fa448.png)

***3.	A on es troba i quin nom rep el fitxer de configuració del SGBD Percona Server?***

Es troba dintre de la ruta /etc/my.cnf i el fitxer rep el nom de my.cnf
![image](https://user-images.githubusercontent.com/61474765/154858698-63db7483-1d34-4518-9876-e02441e38daf.png)


***4.	A on es troben físicament els fitxers de dades (per defecte). Com ho has sabut?***
Es troben dintre de la ruta /var/lib/mysql.
Ho he sabut perquè ve a la documentació oficial a l’hora d’instal·lar-lo de la pàgina del Percona. 
![image](https://user-images.githubusercontent.com/61474765/154858733-2baf9bb6-f967-4b72-a0a3-43c9d57c8fa3.png)

***5.	Crea un usuari anomenat asix en el sistema operatiu i en SGBD de tal manera que aquest usuari del sistema operatiu no hagi d'introduir l'usuari i password cada vegada que cridem al client mysql?
i.	https://dev.mysql.com/doc/refman/8.0/en/password-security-user.html
ii.	Usuari SO-→ asix / patata
iii.	Usuari MySQL → asix / patata***


Usuari Mysql:

![image](https://user-images.githubusercontent.com/61474765/154858865-6a89b9d2-4d1b-4529-b1c2-cf15ffb2f0f0.png)
![image](https://user-images.githubusercontent.com/61474765/154858871-ccc3b4cd-f423-43a9-ae57-c4c4677cb7c5.png)

Usuari SO:
![image](https://user-images.githubusercontent.com/61474765/154858901-707d970f-9677-4e03-99a5-1dfefa75086c.png)

Ara, dintre del arxiu my.cnf posarem el nom d’usuari i la contrasenya per tal de no haver de posar-lo cada vegada que entrem al mysqld, i fem un restart del servei.

![image](https://user-images.githubusercontent.com/61474765/154858917-7470ac2d-c281-453a-b628-cf8104f4941b.png)








