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

1. Åben Putty og kopir ip-adressen på servere, fra Digital Ocean. og indtast den i "Host name(or IP address). port forbliver 22, da det er SSH porten, vi forbinder over.

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

1. Vi starter med at installere den mest basale notepad for linux: Nano

```
yum install nano
```

Kommandoen kørers og den vil give dig et overblik over hvad den henter/installerer, og vi kan bekræfte at det er okay, ved at skrive: y eller yes.

