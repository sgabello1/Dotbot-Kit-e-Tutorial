# DotBot Kit - Set Up del kit "ridotto"



Questo semplice tutorial spiega come usare la piattaforma di cloud robotics con un kit minimale, un Raspberry pi 3 che si comporterà come il vostro robot in versione "ridotta".

__NB: questa è una versione beta e stiamo lavorando per rendere ancora più semplice l'utilizzo della piattaforma! Se hai problemi scrivici a info@hotblackrobotics.com__

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
Quindi inserite il nome della rete (ssid) a cui volete che il Raspberry si connetta e la password necessaria alla connessione con il relativo numero assegnato alla rete
NB: ovviamente nel vostro caso non è detto che l'ID giusto sia il 3 quindi fate molta attenzione!!
```
set_network 3 ssid "Nome-del-Wifi"
set_network 3 psk "La-password-che-serve-per-connettersi"
```
ora 
```
OK
> save
OK
```
Ora digitate enable_network [numero assegnato alla rete - in questo caso 3]

```
> enable_network 3
OK
> save
OK
> reconnect 
OK
> save
OK
```
NB: l'ultimo save dopo reconnect è ESSENZIALE altrimenti non vi salva la rete e tutto quanto fatto fin'ora andrà perso :)
Premete CTR+C per uscire dalla modalità interattiva di wpa_cli e digitate ``` reboot ```  oppure riavviate anche in modo più grezzo togliendo e rimettendo l'alimentazione al Raspberry :)

Ora provate a conntettervi alla piattaforma a www.hotblackrobotics.com/cloud e premendo su connect vedere se si connette.
