# DotBot Kit - Set Up del kit "ridotto"



Questo semplice tutorial spiega come usare la piattaforma di cloud robotics con un kit minimale, un Raspberry pi 3 che si comporterà come il vostro robot in versione "ridotta".

__NB: questa è una versione beta e stiamo lavorando per rendere ancora più semplice l'utilizzo della piattaforma! Se hai problemi scrivici a info@hotblackrobotics.com__


# Copiare l'immagine su SD


Su Ubuntu si eseguono poche operazioni.
Per capire quali device avete sul pc aprite un terminale e digitate:

```
sudo fdisk -l

```

Vi comparirà una cosa del genere

![] (disk1.png) 

Ora inserite l'SD nel PC e confrontando i risultati noterete che c'è un dispositivo in più. Nel mio caso il dispositivo SD è /dev/mmcblk0

![] (disk2.png) 

Ora digitate 

```
sudo dd bs=4M if=/dev/<il vostro device> | gzip > /home/<vostro_nome_utente>/<nome_dell_immagine>`date +%d%m%y`.gz
```
queste istruzioni copieranno dalla SD alla vostra cartella sul pc con percorso: ```/home/<vostro_nome_utente>. ```

Nel mio caso digito *sudo dd bs=4M if=/dev/mmcblk0 | gzip > /home/sgabello/dotbot`date +%d%m%y`.gz*

Perchè l'SD è in /dev/mmcblk0 e /home/sgabello/dotbot è il percorso con nome di dove lo voglio copiare. 
Da notare che la ```dotbot`date +%d%m%y``` salva il nome dotbot con la data attuale in giorno/mese/anno. 
Infatti il mio risultato è dotbot191016 (perchè l'avevo fatto il 19 ottobre 2016).

Perfetto, ora prendiamo la copia da PC e bruciamola sulla nuova SD. 

```
sudo gzip -dc /home/<vostro_nome_utente>/<nome_immagine>.gz |sudo dd bs=4M of=/dev/<dispositivo_SD>
```
Nel mio caso era: 
sudo gzip -dc /home/sgabello/dotbot191016.gz |sudo dd bs=4M of=/dev/mmcblk0. NB: lasciate stare che sotto la voce Device Boot quando fate sudo fdisk -l compare /dev/mmcblk0p1 e /dev/mmcblk0p2 p1 e p2 stanno per partition ma a noi non interessano.



Connettersi al Raspberry
===

Collegarsi ad una rete wifi
===


Pronti a partire!
===
