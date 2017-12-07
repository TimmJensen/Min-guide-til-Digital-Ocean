# Min guide til Digital Ocean

## 1. Oprettelse med github's educationsprogram

1. Start med at gå ind på https://education.github.com, og endten send ansøgning til Githubs Education rabatter eller tryk på "Get the pack", hvis du har fået adgang allerede.

2. Du får nu en oversigt over alle de steder du får rabatter til med Githubs Educationprogram. Du skal bare trykke på "Get your pack", så får du adgang til dem.

3. Find så den rabat der giver dig $50 til [DigitalOcean](www.digitalocean.com/), og tryk på på linket under "Get access". Nu skulle du gerne modtage en rabatkode og et link til Digital Ocean, hvor du så skal oprette dig.

Rabatkoden til digitalOcean, skal indtastes efter oprettelsen af din bruger, på digital Ocean.

## 2. Oprettelsen på Digital Ocean

obs. Du skal tilknytte et kreditkort, får at kunne blive oprettet på Digital Ocean. Dette er kun en sikkerhedsforanstaltning, der bliver __ikke__ trukket for noget, under oprettelsen af brugeren.

1. Start med at udfylde formularen på forsiden af Digital Ocean, til oprettelsen af din nye bruger. Husk at bekræfte din email, hvis du ikke allerede har gjort dette.

2. Når din bruger så er oprettet, skal du så logge ind og trykke på dit avatar oppe i højre hjørne, og vælg "Settings".

3. Ude i venstre side, skal du vælge "Billing" og rulle ned på siden, til du ser "Promo code". i inputfeltet, skal du så indtaste den rabatkode, du har modtaget fra Githubs Educationsprogram og tryk på "Apply code".

Nu har du så modtaget $50, som du kan bruge for.

## Oprettelsen af webserveren

TIP: Oppe i højre hjørne af siden, sidder en "Lyn-knap" til hurtig oprettelse af forskellige services hos Digital Ocean.

1. Tryk på Lyn-knappen "Create" og vælg så "Droplet, Create cloud servers".

2. Til at starte med, skal vi vælge et styresystem. Vi kan vælge imellem 6 gratis linux styresystemer, alle ligegode typisk vælger man ubuntu, debian eller CentOS. I dette eksempel vælger vi CentOS, version 6.9 og x32-bit.

3. Det næste er så at finde ud af hvor meget cpu, plads og data, vi får brug for. Vi vælger den billigste til $5, da vi ikke kommer til at køre noget stort.

Vi kan så vælge at tilføje ekstra plads, men dette får vi ikke brug for i dette eksempel.

4. Så får vi mulighed for at vælge, hvor, vores server skal placeres. Det er en god huske regl, at placere den så tæt på en selv, som muligt. Vi vælger, Frankfurt. nummeret nedenfor, er ikke vigtigt, så der er frit valg.

Vi kan nu vælge nogle ekstra funktioner til serveren, men vær obs. på at det kan koste dig ekstra. Vi vælger ikke noget.

Vi har som det næste mulighed for at tilføje en SSH nøgle til. Vi anvender det ikke, i dette eksemple.

5. Til sidst kan vi vælge hvor mange serverer, vi vil oprette og hvad de skal hedde.

Så er det bare at trykke "Create" og så går din(e) server(e) igang med at installere. 

Du skulle gerne modtage en mail, med information på brugernavn og adgangskode, til at få forbindelse til serveren.

## Forbind til serveren

Når serveren er installeret, kan du se information på server, som ex. serverens IP-adresse.
Herfra kan du også tilkoble et domæne, men det kommer vi ikke til her.

Vi skal bruge et program som hedder "Putty" til at forbinde til serveren, via SSH (Secure Shell). 

Du kan download [Putty her](http://www.putty.org).

1. Åben Putty og kopir ip-adressen på servere, fra Digital Ocean og indtast den i "Host name(or IP address). port forbliver 22, da det er SSH porten, vi forbinder over.

2. Gem denne session, ved at give den et navn under "Saved Sessions" og tryk på "Save". Nu kan du nemmere koble på serveren, ved senere brug.

3. Når du skal opretet forbindelse til serveren, skal du trykke på "Open" i bunden af programmet. Det vil åbne en terminal og prompte dig med en Security Alert. Alerten minder dig bare om, at det kan være en server som udgiver sig for noget som den ikke er. Men i dette tilfælde stoler vi på maskinen og trykker på "Ja".

4. Nu skal du så indtaste det brugernavn, du har modtager i mailen, typisk: root

5. Kopir så den lange adgangskode og "Højre-klik" inde i terminalen og __IKKE ctr+v__ da det ikke vil virke.

6. Skriv indtast nu den lange adgangskode igen, for at bekræfte.

7. Den vil nu have dig til at oprette en ny adgangskode. Gør det og husk at gør den sikker! 

Du har nu forbindelse til serveren! Du kan bekræfte dette ved at der står: 
[root@din-servers-navn ~]#

## Installation af programmer og moduler

Vi skal installere følgene programmer på serveren:

* Nano
* MySQL
* Node.js
* npm
* epel-release

Måden at installere programmer på linux, kan varigerer lidt, fra distribution til distribution.

eksempelvis Ubuntu, bruger man "apt-get" til at installere programmer med.
Vi bruger "SUDO" for at udfører kommandoen med administrative rettigheder.
```
sudo apt-get install npm
```
På CentOS bruger man "YUM" til at installere med.

### 1. Installation af _Nano_
1. Vi starter med at installere den mest basale notepad for linux: Nano

```
yum install nano
```

Kommandoen kørers og den vil give dig et overblik over hvad den henter/installerer, og vi kan bekræfte at det er okay, ved at skrive: y eller yes.

### 2. Installation af _MySQL_

Vi skal installere og opsætte mysql på serveren, så vores kommende hjemmesie, kan forbinde til den. Vi indsætter noget eksempel data, fra en tidligere database (fra Hi-Fi Projektet).

1. Start med at udfører følgene kommando, for at starte installationen af MySQL.

```
yum install mysql-server
```

Igen vil du kunne se hvad kommandoen installere for dig og du skal acceptere ved at skrive "j" eller "Ja". Installationen færdiggøres.

2. Nu skal vi så starte den service vi lige har installeret _MySQL_

Kør kommandoen:
```
service mysqld start
```

Du kan udfører følgene kommandoer for at start, stoppe eller genstarte servicen
```
service mysqld start/stop/restart
```

Du skulle gerne modtage en status: "OK" med grøn skrift, som er et tegn på at den kunne starte, uden problemer.

3. Vi skal nu konfigurere mysql-servicen, så vi oprette forbindelse og anvende databasen uden problemer.

Vi skal kører kommandoen:
```
sudo /usr/bin/mysql_secure_installation
```

Når du har kørt kommandoen, bliver du bedt om at indtaste den nuværende ROOT adgangskode, for at kunne konfigurere _MySQL_. Hvis det ikke er sat et password, skal du bare trykke _ENTER_.

4. Du bliver nu spurgt, om du vil opsætte en ny adgangskode for root-brugeren, til mysql. Vi siger selvfølgelig "Y" eller "YES", da vi gerne vil kunne forbinde til databasen på sikker vis.

indtast nu en ny adgangskode og bekræft.

5. Nu bliver du spurgt om du vil fjerne anonyme brugere og det vil vi gerne, da vi ikke kender til dem og det kan potention blive et sikkerhedsproblem.

6. Denne gang spørger den om du vil tillade at, der kan bliver oprettet forbindelse til databasen, ved fjernkontrol. Det vil vi også meget gerne kunne, da vi skal overfører data til dens database. Så her svarer vi _NEJ_

7. og til næst sidst, vil vi meget gerne fjerne nuværende _test_ databaser.

8. til sidst vil vi gerne genindlæse tilladelser.

Så er MySQL sat op på serveren korrekt.

### 3. Installation af Node.js

1. Vi starter med at installere alle nødvændighederne for at kunne kører node.js korrekt på serveren.

Kør følgene kommandoer:
```
yum install epel-release
yum install nodejs
yum install npm
```

2. Vi skal også lige installere et module til node, som vil holde vores node.js opdateret.
```
npm install -g n 
```

3. Nu skal vi så lige opdatere node før vi går igang med at bruge det.

```
n lts
```

Så får at tjekke versionen af node: køres kommandoen:

```
n
```

Får at komme ud af "Tjek versionen" trykker du på __CTRL + C__

__Genstart din linux-box nu, før du fortsætter.__


### 4. installation af PM2-modulet.

Vi installere et modul kaldet "PM2", som kan start og overvåge vores server og dens filer, med andre ord, PM2 er en process manager til Node.js applikationer.

1. For at installere PM2, kør kommandoen:
```
npm install -g pm2
```

2. For at starte PM2's process:
```
pm2 startup
```

### 5. Installation af __GIT__

Vi skal installere __GIT__ så vi kan clone, pull og evt. push til github.

1. Installer GIT ved at kører:
```
yum install git
```

2. Konfigurer GIT ved at tilføje navn og email:

```
git config --global user.name "Dit navn"
git config --global user.email "din@email.dk"
```

3. Vi kan tjekke konfigurationen ved at skrive:
```
nano ~/.gitconfig
```

og lukke den igen ved: CTRL + X

### 6. Opret et nøglesæt til at logge ind på GitHub
Vi skal oprette en SSH-key fra serveren, så vi kan forbinde til vores Github konto.

1. Opret en SSH key:
```
ssh-keygen -t rsa
```

2. Kopir din SSH-key:
```
cat ~/.ssh/id_rsa.pub
```
Kopier indholdet af den offentlige nøgle til GitHub -> Settings -> SSH and GPG keys -> New SSH key

### 7. Opret en mappe til din applikation

1. start med at oprette en mappe:

```
mkdir ~/www
```

Naviger ind i mappen
```
cd ~/www
```

### 8. Klon dit repository fra GitHub

1. Clon et repository:
```
git clone git@github.com:brugernavn/repository 
```

2.  Opdater det clonede repository:
```
git pull git@github.com:brugernavn/repository master
```


### 9. Opsæt databasen
[hent mysql workbench](https://www.mysql.com/products/workbench/)

1. Start med at opsætte mysql på linuxmaskinen:
```
mysql -p
```

og indtast nu det password vi sat for root.

2. Nu skal vi give tilladelse til at logge ind og fortage handlinger på mysql, på andre ip-adresser, end localhost.

```
GRANT ALL ON *.* to 'root'@'%';
```

Du skulle gern modtage status: "Query OK"

3. Vi opretter nu et nyt kodeord for root, så vi kan logge ind fra fjernt. Vi kan vælge at bruge den samme kode eller en helt ny kode.

```
SET PASSWORD FOR 'root'@'%' = PASSWORD('root');
```
og for at komme ud af mysql terminalen:
```
quit
```

4. Åben nu mysql workbench, og tilføj en ny forbindelse

5. vi skal nu oprette et nyt schema (database). Dette gøres ved at klikke på database ikonet, nr. 4 fra venstre, i top baren.

6. Giv den et navn: "hifi" og tryk "APPLY"

et nyt vindue skulle gerne poppe frem.

7. Tryk apply igen og close, hvis alt er okay.

8. opret nu forbindelse til din nuværende database (lokalt), og marker hifi-databasen.

9. tryk nu på server og "Data export"

10. vælg databasen og tryk på start export.

11. Så skal vi ind på den forrige session, altså serverens database. og gøre det samme step, dog vælg import denne gang.

12. lokaliser mappen, du har exporteret dataen til og vælg import.

Du har nu dataen i  den nye database.





# De små tricks

* Hvis importen af databasen fejler, prøv med med direkte input via query.

* Hvis importen af data via query fejlermelder med: database ikke valgt.

Over accesstoken skriv: USE [databasenavn]