+++
date = "2016-08-02T16:38:11+02:00"
title = "GleSYS"
toc = true
weight = 25
+++

{{% notice info %}}

The older UTN servers are hosted by [GleSYS](https://glesys.com). As these
servers where still managed by Swedish System Administrators, they made the
following documentation in Swedish. Most of these servers have/been or are
planned to be removed.

{{% /notice %}}

## Inledning

UTN har idag ett flertal olika servrar hos hosting företaget Glesys
([www.glesys.com](https://glesys.com)). På dessa virtuella servrar hanterar vi all mjukvara i form av
operativsystem och program som är installerade. Loggar man in i
användargränssnittet via glesys.com kan man lätt klona en server för att på så
sätt skapa en ny identisk kopia, byta IP-adresser och även modifiera hårdvaran i
form av exempelvis antal processorkärnor och RAM-minne.

## Lista över servrar

### webhost.utn.se - [REMOVED]

På denna server finns idag UTN:s medlemsregister.

- Ubuntu 10.04 	LTS
- Apache-webserver

Hosting:

- UTN:s medlemsregister (register.utn.se)


Anledningen till att den gamla servern inte längre används är flera.

- Den börjar bli utdaterad rent mjukvarumässigt och ingen har full koll på vad
som är installerat på den. Det är lite riskabelt att uppdatera mjukvaran pga
detta.
- Det finns väldigt lite dokumentation hur den är konfigurerad.
- Den har en tendens att krascha vid hög belastning.
- Dess hårddisksutrymme minskar ständigt bland annat pga växande loggfiler.


### main.utn.se - [REMOVED]

UTN:s hemsida

Programvara:

- Ubuntu 12.04 LTS
- nginx som webserver.

Hosting:
- www.utn.se

### sections.utn.se - [DEPRECATED]
Some of UTN:s sections have hosting on utn.se. Many also have test-sites that never where published. Most of the sites uses the www.utn.se drupal CMS as their template.

Programvara:

- Ubuntu 12.04 LTS
- nginx som webserver.

Hosting:

- bas.utn.se
- es.utn.se
- k.utn.se
- sts.utn.se
- w.utn.se

### event.utn.se - [REMOVED]

UTN:s olika events hemsidor.

Programvara:
- Ubuntu 12.04 LTS
- nginx som webserver.

Hosting:
- anmalan.rally.utn.se
- anmalan.polhacks.utn.se
- anmalan.forsranningen.utn.se
- anmalan-balen.utn.se

No longer hosting:
- balen.utn.se
- basar.utn.se
- forsranningen.utn.se
- klubbverket.utn.se
- polhacks.utn.se
- rally.utn.se
- recce.utn.se
- utnarm.utn.se
- match.polhacks.utn.se

### files.utn.se

Används för UTN:s filhanteringssystem Owncloud (En open source dropbox-klon:
https://owncloud.org/).

Mukvara:

- Ubuntu 12.04 LTS
- nginx

Hosting:

- Owncloud fileserver (files.utn.se)

### utnarm.utn.se - [REMOVED]

Utnarms gamla hemsida låg här. De har numera flyttat över till Drupal på
event.utn.se. Borde raderas, hör med utnarm om denna fortfarande används.

Mjukvara:

- Ubuntu 12.04 LTS
- nginx
- Ruby server

Hosting:
- Utnarms hemsida (utnarm.utn.se)

### pay.utn.se

UTN:s server för betaltjänster. Ett egenutvecklad system av Åke Lagercrantz och
Niclas Edenvin.

Mjukvara:

- Ubuntu 12.04 LTS
- nginx

Hosting:

- UTN:s betaltjänst (pay.utn.se)

## Nya servrarna

Alla nya servar har en standardinstallation av ubuntu 12.04, samt nginx med
vissa modifikationer. Guiden som använts för att konfigurera och installera allt
på servrarna kommer från teknikbloggen Arstechnica för den som är intresserad:
http://arstechnica.com/series/web-served/ (del 1-3 samt delar av del 4).

Detta gäller servrarna:

- main.utn.se
- files.utn.se
- sections.utn.se
- event.utn.se
- pay.utn.se

### Databashantering

Varje server har en administratörsida med programmet phpmyadmin för att hantera
databaserna på serverna. Användarnamn och Lösenord hittar du i dokumentet det
gemensamma lösenordsdokumentet på Google Drive. Du når databasen på:

- https://[servername].utn.se/utndb

### Uppdatera servern

Att uppdatera serverns mjukvara är väldigt enkelt, med jämna mellanrum bör
följande två kommandon köras:

- `sudo apt-get update`
- `sudo apt-get upgrade`

Där första kommandot uppdaterar listan över tillgängliga uppdateringar, och det andra kommandot uppdaterar alla program som är utdaterade.

### Enkla kommandon för program och server
- Starta om servern: `sudo reboot`
- Starta om webservern nginx: `sudo service nginx restart`
- Ladda om inställningarna för nginx: `sudo service nginx reload`
- Starta om PHP: `sudo service php5-fpm restart`

### Backup

Företaget Glesys som hanterar servrarna tar dagligen backuper av alla filer som
finns på servrarna. Så om något skulle råka raderas kan Glesys återställa
enskilda filer och även hela servern till en tidigare tidpunkt. För att
återställa filer ringer eller mailar man till glesys kundsupport,
kontaktuppgifter finns på deras hemsida.

Enskilda databaser är något Glesys inte kan återställa utan att också behöva
återställa hela servern. Därför tas det daglig backup av programmet
automysqlbackup som skapar .sql-filer för varje databas och sedan sparar dem i
katalogen, `/var/lib/automysqlbackup`. Denna backup körs en gång per dag och
sparar allt eftersom i tre olika mappar, daily, weekly och monthly.

### Skapa en ny hemsida

För att skapa en ny hemsida finns det 4 olika steg:

1. Skapa en användare som kan logga in och hantera hemsidan.
2. Skapa en katalog till hemsidan.
3. Skapa en konfigurationsfil till webservern nginx.
4. Skapa en databas till hemsidan.

Vi kommer i detta exempel visa hur man skapar en sida åt UTN:s event Utnarm.

#### 1. Skapa en ny användare

Logga in på servern via ssh och kör kommandot: `adduser utnarm-utn-se`.
Därefter får man fylla i personuppgifter till den hemsideansvariga, vilket kan
vara användbart så att systemadministratören vet vem man ska ringa eller maila
om problem uppstår. För att underlätta hanteringen av användare bör
namnkonvention användas, se nedan.

**Kommittéer och andra grupper:**

Dessa bör ha samma namn som hemsidan, exempelvis hemsideansvarig för Utnarm bör
ha användarnamnet: `utnarm-utn-se`. Exempel på personuppgifterna på grupper:

```
Name: Web Utnarm
Other: web@utnarm.utn.se
```

**Privatpersoner:**

Ibland behöver specifika IT-kunniga personer ha tillgång till servern för att
administrera flera olika sidor, dessa bör använda konventionen:
fornamn-efternamn Om en privatperson ska få administratörsrättigheter, kör man
följande kommando:

`sudo usermod -a -G sudo fornamn-efternam`

Var dock väldigt restriktiv med att ge personer administratörsrättigheter,
vanliga hemsideansvariga m.m. borde inte behöva sådana rättigheter för att
utföra sitt jobb. Varje person med admin-rättigheter är en potentiell
säkerhetsrisk och bör bara ges till personer man litar på.

#### 2. Skapa en ny katalog

Hemsidorna sparas som standard i mappen `/var/www`, där varje hemsida får en
mapp med hemsidans adress samt en undermapp kallad public. Exempelvis heter
Utnarms mapp ”utnarm.utn.se”. För att skapa en mapp, gå först till `/var/www`

`cd /var/www`

Därefter skapa hemsidans mapp:

`sudo mkdir utnarm.utn.se`

Därefter skapa undermappen public:

`sudo mkdir utnarm.utn.se/public`

Nu ska vi se till att enbart Utnarms användare samt webservern kommer åt denna
katalog.

Börja med att gå in i katalogen:

`cd utnarm.utn.se`

Kör därför kommandot:

`sudo chown -R utnarm-utn-se:www-data ./`

Detta gör att mapparna ägs av användaren utnarm-utn-se och gruppen www-data
(vilket är den grupp webservern tillhör). Därefter ska vi se till att endast
Utnarm och webservern får rätt rättigheter till mappar och filer.

`find ./ -type d -exec chmod 750 {} \;  # Change directory permissions rwxr-xr-x`

`find ./ -type f -exec chmod 640 {} \;  # Change file permissions rw-r--r--`


Nu kan användaren utnarm läsa och skapa/ändra filer, samt öppna alla mappar och
gruppen www-data kan läsa filer och öppna mappar, men inte skapa/ändra filer. Om
detta skulle behövas för en specifik mapp eller fil, byt ut 750 till 770 i det
översta av de två kommandona.

#### 3. Skapa en konfigurationsfil

Om man besöker mappen `/etc/nginx` kommer man till webservern nginx och dess
konfigurationsfiler. Alla aktiva hemsidor finns i mappen `sites-enabled`, i den
mappen finns en länk till en textfil med inställningar för hemsidan. Anledningen
till att man bara har länkar i en mapp och inte orginaltextfilen, är för att man
ska lätt kunna inaktivera en hemsida utan att behöva radera hela
konfigurationsfilen, då kan man istället bara ta bort länken. Den riktiga
textfilen finns i mappen `sites-available`.

Om vi nu ska skapa en ny hemsida, räcker det med att vi går in i mappen
`sites-available`

`cd /etc/nginx/sites-available`

därefter kopierar man en standardfil för UTN-sidor med de vanligaste
inställningarna och döper kopian till den nya hemsidans namn.

`sudo cp utn-default utnarm.utn.se`

Nu kan du redigera textfilen för att inställningarna ska stämma för den nya
sidan i en texteditor.

Exempelvis nano: `sudo nano utnarm.utn.se`

Gör dina ändringar, därefter spara med *ctrl+x* och därefter tryck *y* för att
skriva över gamla filen. Nu ska det skapas en länk till filen i mappen
`sites-enabled` för att den nya sidan ska börja fungera.

`sudo ln -s /etc/nginx/sites-available/utnarm.utn.se /etc/nginx/sites-enabled`

Nu är allt klart, då ska vi bara starta om nginx

`sudo service nginx reload`

#### 4. Skapa en databas

För att skapa en databas kan vi använda programmet phpmyadmin, som man hittar på
respektive servers administratörs-sida.

Logga in och klicka på **”Användarna” → ”Lägg till en användare”**
```
Användarnamn: utnarm
Server: localhost
Lösenord:
```
Klicka därefter i rutan: **”Skapa databas med samma namn och tilldela alla privilegier”**.

Klart!

### HTTPS och säkerhetscertifikat

UTN:s servrar använder sig av ett så kallat wildcard (\*.utn.se)
SSL-certrifikat. Detta innebär att alla adresser som slutar med utn.se
(exempelvis utnarm.utn.se) kan använda detta certifikat för att kryptera
anslutningen till servern. Detta är viktigt om man exempelvis ska logga in på en
hemsida eller utföra internetbetalningar för att ingen ska kunna avlyssna
anslutningen och på så sätt sno lösenord m.m.

Certrifikaten finns sparade i katalogen `/etc/ssl/private/utn/`

Det är ytterst viktigt att filerna i denna katalog inte kommer i fel händer!
Detta skulle kunna få allvarliga konsekvenser för all UTN:s IT-verksamhet. Det
är därför enbart root-användaren som ska vara ägare och den enda root-användaren
den enda som ska kunna läsa filerna.

Certifikatet uppdateras regelbundet, just nu uppdateras det vart 4:e år, och är
giltigt i fyra år och två månader, nuvarande certifikatet är giltigt till
2016-10-14. Tidigare har företaget GeoTrust använts och de har kontaktat vice
ordförande på ekonomi@utn.se när det närmar sig för en uppdatering.
