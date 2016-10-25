# DotBot Kit - Set Up del kit "ridotto"



Questo semplice tutorial spiega come usare la piattaforma di cloud robotics con un kit minimale, un Raspberry pi 3 che si comporterà come il vostro robot in versione "ridotta".

__NB: questa è una versione beta e stiamo lavorando per rendere ancora più semplice l'utilizzo della piattaforma! Se hai problemi scrivici a info@hotblackrobotics.com__

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

Oppure provate direttamente ad entrare in piattaforma scrivendo sul browser del vostro computer
```
http://dotbot.local/
```
Se entrare nell schermata iniziale di Dotbot funziona tutto correttamente! 

Pronti a partire!
===
