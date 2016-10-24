# DotBot Kit - Tutorial



Questo semplice tutorial spiega come usare la piattaforma di cloud robotics con un kit minimale, un Raspberry pi 3 che si comporterà come il vostro robot in versione "ridotta".

** NB: questa è una versione beta e stiamo lavorando per rendere ancora più semplice l'utilizzo della piattaforma! Se hai problemi scrivici a info@hotblackrobotics.com **

![] (rapseberry3.jpg) 


# Copiare l'immagine su SD


Su Ubuntu si eseguono poche operazioni.

- Per capire quali device avete sul pc aprite un terminale e digitate:

```
sudo fdisk -l

```

Vi comparirà una cosa del genere

![] (disk1.png) 

- Ora inserite l'SD nel PC e confrontando i risultati noterete che c'è un dispositivo in più. Nel mio caso  il /dev/mmcblk0

![] (disk2.png) 

- Ora digitate 

```
sudo dd bs=4M if=/dev/il vostro device | gzip > /home/vostro_nome_utente/image`date +%d%m%y`.gz
```
e il 




Connettersi al Raspberry
===

Collegarsi ad una rete wifi
===


Pronti a partire!
===
