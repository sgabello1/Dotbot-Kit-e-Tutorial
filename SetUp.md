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

Nel mio caso digito ```sudo dd bs=4M if=/dev/mmcblk0 | gzip > /home/sgabello/dotbot`date +%d%m%y`.gz```

Perchè l'SD è in ```/dev/mmcblk0``` e ```/home/sgabello/dotbot``` è il percorso con nome di dove lo voglio copiare. 
Da notare che la ```dotbot`date +%d%m%y``` salva il nome dotbot con la data attuale in giorno/mese/anno. 
Infatti il mio risultato è dotbot191016 (perchè l'avevo fatto il 19 ottobre 2016).

Perfetto, ora prendiamo la copia da PC e bruciamola sulla nuova SD. 

```
sudo gzip -dc /home/<vostro_nome_utente>/<nome_immagine>.gz |sudo dd bs=4M of=/dev/<dispositivo_SD>
```
Nel mio caso era: 
```
sudo gzip -dc /home/sgabello/dotbot191016.gz |sudo dd bs=4M of=/dev/mmcblk0 
```  

NB: lasciate stare che sotto la voce Device Boot quando fate ```sudo fdisk -l``` compare ```/dev/mmcblk0p1``` e ```/dev/mmcblk0p2``` p1 e p2 stanno per partition ma a noi non interessano.



Connettersi al Raspberry
===
Prendete un monitor e collegatelo al connettore HDMA del vostro Raspberry poi collegate anche una tastiera (il mouse non serve siccome non c'è interfaccia grafica). 
Effettuate il login con le seguenti credenziali (nome utente e password):
```
user: root
password: raspberry
```
Ok ora connettiamoci alla rete wifi di casa vostra!

Collegarsi ad una rete wifi
===
Digitate sul terminale 
```
wpa_cli
```
una cosa simile a questa apparirà sul terminale
```
Selected interface 'wlan0'

Interactive mode
```
Quindi scansionate le reti intorno a voi con
```
> scan
```
e successivamente visualizzate i risultati della scansione

```
> scan_results
```
Otterrete qualcosa del genere
```
> scan
OK
<2>CTRL-EVENT-SCAN-RESULTS
> scan_results
bssid / frequency / signal level / flags / ssid
00:55:ab:25:ac:5a	2462	-71	[WPA2-PSK-CCMP][ESS]	WLAN-Network
00:11:99:51:ba:f0	2437	-64	[WPA2-PSK-CCMP][ESS]	WLAN-Network2
>
```
NB: se la rete a cui vi volete connettere ha si [WPA2-PSK-CCMP] che [WPA-PSK-CCMP] è possibile che abbiate problemi! Dovreste disabilitare la funzionalità [WPA-PSK-CCMP] nell'hotspot.(Provate a creare un hotspot con il cellulare con solo [WPA2-PSK-CCMP] per verificare che il problema è quello. Se funziona il tutorial significa che dovrete cambiarlo anche nella rete che volete configurare.)

Quindi aggiungete la rete alla quale volete connettervi
```
> add_network
```
Questo comando vi restituirà un numero ad esempio
```
> add_network
3
```
Quindi inserite il nome della vostra rete (ssid) e la password con il relativo numero assegnato alla rete
```
set_network 3 ssid "Wifi-casa"
set_network 3 psk "Lamiapasswordsegreta"
```
ora 
```
OK
> save
OK
> enable_network 3
OK
> save
OK
> reconnect 
```
Premete CTR+C per uscire dalla modalità interattiva di wpa_cli e digitate ``` reboot ```  oppure riavviate anche in modo più grezzo togliendo e rimettendo l'alimentazione al Raspberry :)

Ora per verificare che effettivamente tutto funzioni e sia configurato correttamente vediamo se siete connessi al nome della rete ssid che avete scelto

```
nm-tool | grep \*
```

Se compare il nome della vostra rete funziona tutto perfettamente!

Pronti a partire!
===
