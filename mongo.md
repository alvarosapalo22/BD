# ***PART III - INSTAL·LACIÓ SGBD MongoDB (màx. 1 punt)***

## INSTAL·LACIÓ

*Com sempre, primer farem un sudo yum Update per descarregar els arxius*

![image](https://user-images.githubusercontent.com/61474765/154860891-5d3a29fe-7515-43a6-936b-9882e00f97c4.png)

*Ara, crearem un arxiu dintre de la ruta /etc/yum.repos.d/mongodb-org-5.0.repo per tal de poder instal·lar el MongoDB directament utilitzant el yum.*

![image](https://user-images.githubusercontent.com/61474765/154860906-65a4fbe4-75ff-420a-b4e8-48d305577fb6.png)

 *I aquet serà el contingut del arxiu.*

![image](https://user-images.githubusercontent.com/61474765/154860926-5936cc30-babb-4325-906b-883f0c3b1a1e.png)

*Descarregarem l’ultima versió del MongoDB, amb la següent comanda: sudo yum install -y mongodb-org.*

![image](https://user-images.githubusercontent.com/61474765/154860940-50d24879-7556-4093-b3d2-7b4e6ac6d160.png)

*Ara, el que farem es iniciar el servei del MongoDB, per això farem la comanda sudo systemctl start mongod, i farem un systemctl start mongod per comprovar l’estat.*

![image](https://user-images.githubusercontent.com/61474765/154860957-3fa27003-0608-4cfe-85a2-7c66569d545f.png)

*Si posem Mongo, en la màquina virtual comprovem que ens entra perfectament.*

![image](https://user-images.githubusercontent.com/61474765/154860970-4b6c3fb1-b484-4439-ada5-d0158f4fc678.png)

*Ara, entrarem dintre del arxiu /etc/mongod.conf i on posa #security afegirem una línia que posarà authorization: enabled per tal de activar el usuaris amb contrasenya.*

![image](https://user-images.githubusercontent.com/61474765/154860980-fe767d49-72f3-4619-a660-886144c7f399.png)

*I fem un restart del servei.*

![image](https://user-images.githubusercontent.com/61474765/154860993-ef2dea35-4437-4f6b-96a0-0aff6e4efadd.png)

*Ara, ens connectarem de nou al Mongo per tal de crear un usuari, posarem use admin per entrar amb mode administrador. Un cop dintre crearem un usuari que li hem anomenat root amb contrasenya patata.*

![image](https://user-images.githubusercontent.com/61474765/154861013-82154bb2-bc8f-4b6a-bd41-fe1a8498f3f9.png)
![image](https://user-images.githubusercontent.com/61474765/154861018-21a762d9-4e71-4c74-a7f3-c48f117e498d.png)

*Ara, ens connectarem al Mongo per comprovar que l’usuari s’ha creat correctament*

![image](https://user-images.githubusercontent.com/61474765/154861039-1df0ff46-2678-472a-8bbb-3901222e7ebd.png)

*Ara, entrarem dintre del arxiu /etc/mongod.conf i en l’apartat on posa bindIP posarem 0.0.0.0 per tal de poder connectar-nos remotament*

![image](https://user-images.githubusercontent.com/61474765/154861047-841f292c-468d-41c9-90ad-4c16f1e02ec6.png)

*I fem un restart per tal de que agafi les configuracions noves.*

![image](https://user-images.githubusercontent.com/61474765/154861064-c8835b90-f3da-4d33-9d1f-4c434cc1ed49.png)

*Només ens faltarà configurar el Firewall amb el port que toqui per tal de poder connectar-nos.*

![image](https://user-images.githubusercontent.com/61474765/154861074-0142f701-117f-4f8a-9d9c-308af06e35ce.png)

*Ara, provarem de connectar-nos amb la aplicació Robo 3T.*

![image](https://user-images.githubusercontent.com/61474765/154861087-cdfe4290-6ae4-40b5-a42b-9a0e17613dbd.png)
![image](https://user-images.githubusercontent.com/61474765/154861092-87ae4a3e-ee75-4766-bbcb-3722418d491e.png)

*Ens connecta correctament*
