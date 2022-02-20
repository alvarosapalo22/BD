# *Part II - INSTAL·LACIÓ SGBD MySQL 8.0 (màx. 2 punt)*

## INSTAL·LACIÓ
*Com sempre primer descarregarem els paquet amb un sudo yum Update*

![image](https://user-images.githubusercontent.com/61474765/154860272-c0eabeb9-d6bd-491b-a0d1-e34b4e35b2f8.png)

*Primarament, descarregarrem i agregarem el repositori de Mysql amb la comanda sudo wget https://repo.mysql.com/mysql80-comunnity-release-el7-1.noarch.rpm*

![image](https://user-images.githubusercontent.com/61474765/154860291-953db100-0544-402b-aaa0-640d22c29db6.png)

*Ara, instal·larem el paquet descarregat anteriorment utilitzant yum localinstall mysql80-community-release-el7.1.noarch.rpm.
Posarem y cada vegada que ens ho demani.*

![image](https://user-images.githubusercontent.com/61474765/154860300-8dbedac4-85e1-4210-b119-49d2c455c8ab.png)

*Instal·larem l’última versió del Mysql que es la 8.0 amb la comanda: sudo yum install mysql-community-server.
Posarem y quan ens ho demani.*

![image](https://user-images.githubusercontent.com/61474765/154860313-795418e7-7a8d-4bce-a291-bc80db5efb82.png)

*El que farem ara, es iniciar el servei i comprovar que s’inicia correctament fent ser un: sudo systemctl start mysqld. I per comprovar l’estat farem un sudo systectl status mysqld.*

![image](https://user-images.githubusercontent.com/61474765/154860330-873130a7-38bd-40b7-b695-21f282864961.png)

*Comprovem també que podem entrar al mysql perfectament fent servir la comanda mysql -u root -p*

![image](https://user-images.githubusercontent.com/61474765/154860346-e2b98c6d-fef8-43bb-855a-d930009d8a60.png)

*Ara, li definim una contrasenya al usuari root.*

![image](https://user-images.githubusercontent.com/61474765/154860375-a1f1cf54-32ae-4c16-a87f-5486cb247f3a.png)

*Ara, habilitarem el Firewall per tal de poder permetre la connexió amb la nostra màquina Workbench.*

![image](https://user-images.githubusercontent.com/61474765/154860390-7d7d8a2c-9b38-4cda-8933-863bc4f6e5d1.png)

## *RESPON O COMPROVA ELS SEGÜENTS APARTATS*

*1.	A on es troben físicament els fitxers de dades?*

Es troba dintre de /var/lib/mysql.

![image](https://user-images.githubusercontent.com/61474765/154860452-d8ad5170-c6f4-431e-80ef-4be7af72d045.png)

*2.	A on es troba el fitxer de configuració? Quin és el seu contingut?*

Es troba dintre de /etc/my.cnf

![image](https://user-images.githubusercontent.com/61474765/154860595-e1301221-b3a4-41b3-ba0f-1a93704a9327.png)

*3.	El procés de mysqld escolta al port 3306. Quina modificació/passos caldrien fer per canviar aquest port a 33306 per exemple? Important: No realitzis els canvis. Només indica els passos que faries.*

Haurem de entrar dintre del arxiu my.cnf i afegirem sota del [mysqld] port = i el numero del port que volem.

![image](https://user-images.githubusercontent.com/61474765/154860618-cac34f1a-b785-4363-a164-a33e649f3012.png)

Un cop fet, guardarem la configuració i farem un restart del servei.

![image](https://user-images.githubusercontent.com/61474765/154860627-ff0ed609-34bd-4e1d-ad37-c3f8c5a6e8dc.png)

*4.	Un cop finalitzada la instal·lació i veure que funciona, mostra el resultat de la comanda:
ps -ef | grep mysql*

![image](https://user-images.githubusercontent.com/61474765/154860639-ebe0a63b-7d6f-4245-8297-f2238732c39b.png)

*5.	Quines són les característiques principals que ofereix MySQL 8.0 enfront de la 5.7.*

La principal diferencia, es que en versions anteriors per poder entrar al mysql per primera vegada una vegada instal·lat havíem de generar una contrasenya temporal com hem fet en la part 1, cosa que en les noves versions no fa falta entrar amb la contrasenya temporal perquè ens entra el primer cop sense contrasenya.

*6.	Ensenya al professor que us podeu connectar al SGBD.*

![image](https://user-images.githubusercontent.com/61474765/154860702-1efacb97-f477-4892-8797-b21a51f6e42a.png)






