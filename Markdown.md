# Labbmiljö, Git, CLI  & AI

## 1. Labbmiljö

### 1.1 Virtuella maskiner

I uppgiften skapade jag en virtuell labbmijlö med två Linuxmaskiner och en Windows i Virtualbox.
Utav dessa 3 maskiner valde jag att använda en linux server sedan de andra 2 som Ubuntu & Windows desktop.

Syftet med labbmijön är att kunna konfigurera nätverk mellan maskiner och sedan testa kommunikation, filhantering, behörigheter och olika kommandoradsverktyg.
![alt text](<Ubuntu server & desktop ping.png>)![alt text](<Windows powershell ping.png>)
### 1.2 Nätverksplan

![alt text](Nätverksschema.png)
## 2. Nätverkskonfiguration

### 2.1 Ubuntu Server

För att konfigurera en statisk IP-adress på Servern ändrade jag i Netplan-konfigurationen.
Jag öppnade konfigurationsfilen med kommandot:
sudo nano /etc/netplan/00-installer-config.yaml
i konfigurationen ändrade jag dhcp4 & dhcp6 från true till false.
Anledningen är att jag inte vill att servern ska få en IP-adress automatiskt via DHCP. Därav angav jag också den statiska valda IP-adressen.
addresses:
 - 192.168.10.20/24
Efter detta kontrollerade jag att det faktiskt var iå adressen via kommandot "ip a"
### 2.2 Ubuntu Desktop

I ubuntu desktop följde jag samma kommandon som i servern, problemet här blev att jag glömde bort att ändra IP-adressen till den valda linux desktop adressen istället tog jag serverns ip adress vilket skapade ett problem som tog tid att hitta. Jag använde flertal felsökningskommandon som AI rekommenderade. Tillslut fick jag upp ett tips i terminalen som var ett kommando som visade att ip adressen redan var tilldelad.
IP-adressen.
addresses:
 - 192.168.10.21/24
### 2.3 Windows Desktop

I windows använde jag mer AI som stöd eftersom jag har dålig erfarenhet och kunskap av powershell, så för att tilldela internet, skapa mappar, ge behörighet på filer. Fick jag stor handledning. Inga fel dök upp efter jag följde AI rekommendationer. 
IP-adressen.
addresses:
 - 192.168.10.22/24
### 2.4 Test av kommunikation

Se bild där jag pingar alla maskiner till varandra
![alt text](<Ubuntu server & desktop ping.png>)![alt text](<Windows powershell ping.png>)
## 3. Mappar, filer & rättigheter

Att skapa mapparna på Server var väldigt lätt då jag övat på det innan till antagningsprovet. För att se till att rättigheterna blev rätt och att mapparna är ägda av rätt användare syns i bilden.

Återigen för windows använde jag mig av AI för at förstå hur och vad de hänvisade kommandon gjorde.
Bilderna här ser vi mapparna och deras rättigheter.
![alt text](<Ubuntu mappar och rättigheter.png>) ![alt text](<Windows Mappar och rättigheter.png>)
## 4. Git

För att underlätta mina uppdateringar till github valde jag att göra ett skript där jag endast kunde skriva ett enkelt kommando för varje uppdatering!
### 4.1 Skript för uppdateringar
[text](update.sh)
##  5. AI-stöd och kritisk utvärdering

### 5.1 AI-prompt "gemini"

Du ska agera som en erfaren, uppmuntrande och pedagogisk lärare i nätverksteknik och operativsystem. Din elev är en helt ny student som precis har börjat sina studier och behöver lära sig grunderna från botten. 
När jag anger ett kommandoradskommando (t.ex. 'chmod', 'traceroute', 'grep') eller ett begrepp/en funktion inom nätverk och behörigheter (t.ex. 'DNS', 'SSH-nycklar', 'SUDO', 'Subnätmasker'), vill jag att du förklarar det enligt följande struktur: 
Vid varje begrepp förklara i steg för steg utav avbrott, få eleven att använda virtual box och cisco packet tracer , för att följa dina Hänvisningar och lära sig under processen.
### 5.2 Bilder av AI-svar
![alt text](<AI svar.png>) ![alt text](<AI svar 2.png>)
### 5.3 Utvärdering av AI-svar
Svaret på prompten var kortfattat och gav öppningar för vidare frågor, uppgifter & utmaningar. Däremot följde inte AI:n kommandot att fortsätta oavbrutet med steg-för-steg instruktioner, utan gav en mer generell förklaring. 
Det hade varit mer pedagogiskt att bryta ner varje begrepp i mindre delar och ge konkreta exempel på hur man kan använda dem i praktiken, särskilt med tanke på att eleven är nybörjare.
I AI svar 2 på frågan "ge mig en färdig kod exemplar i linux" att  AI gav ett skript på ping och förklarar hyvsatt del för del men hoppar över många tecken såsom "read -p, -c, -eq" vilket för en nybörjar student kan vara förvirrande.
Det hade varit bättre att inkludera dessa tecken och ge en mer detaljerad förklaring av deras funktion och betydelse i skriptet.

