# Penetraatiotestaus raportti

## 1. Johdanto 

Raportin tarkoituksena on selventää havaittuja heikkouksia ja vaaroja nettisivulla. 

Testaukseen käytetään yksi päivä (noin. 4 tuntia) ja testausympäristönä toimii Virtual Machine jossa toimii Kali. Myös Dockeria ja Zaproxya käytetään testauksessa. 

**Päivitys 5.3.2025**

Jatketaan testaamista päivitetyllä sivustolla.

## 2. Yhteenveto 

Käyttäjien taulukkoon oli helppo lisätä käyttäjiä hyökkäyksen avulla. Myös salasanat eivät olleet suojattuja ja nettisivuja pystyi käyttämään käyttäjänimenä. Tämä on suuri riski. Myös taulukosta oli helppo poistaa käyttäjiä SQLI:n avulla. 

Rekisteröinnissä ei tarvinut käyttää vahvaa salasanaa ja syntymäpäiväksi pystyi jopa laittamaan tulevaisuudessa olevan päivän. 15-vuotiaan ikärajakaan ei siis toiminut. 

Virheilmoitus nettisivulla saattaa jakaa sensitiivistä informaatiota käyttäjästä.

**Päivitys 5.3.2025**
Toinen testauskerta

## 3. Löydökset ja löydöksien kategoriointi 

Punainen: 

Käyttäjien taulukkoon pystyi lisäämään hyökkäyksen avulla nettiosoitteita ja erilaisia komentoja. Tämä on kriittinen haavoittuvuus jota voi käyttää hyväksi erinäisten komentojen syöttämiseen. 

Punainen: 

Salasanat eivät olleet suojattuna SQL taulukossa, joten sieltä on helppo kalastella käyttäjätunnuksia. 

Keltainen: 

Vahvan salasanan määritelmää ei ollut. Täten salasanoja on helppo jopa arvaillakkin tai käyttää Brute-Force hyökkäystä. 

Vihreä: 

Rekisteröinnissä ei tarvinut olla 15-vuotias. Rekisteröinti ei tarkistanut ikää vaan antoi sen olla vaikka negatiivinen, eli henkilö olisi voinut syntyä vaikka tulevaisuudessa. 

**Päivitys 5.3.2025**

Sivuille oli tullut mahdollisuus luoda automaattinen turvallinen salasana. Hyökkäyksessä kuitenkin onnistui lisäämään databaseen useita käyttäjiä joiden käyttäjänimet saattoivat olla osoitteita. Myös salasanat eivät olleet suojattuja

Rekisteröinti ei vielä ottanut huomioon ikää, mutta se on vihreän tason heikkous.

## 4. Liitteet

ZAP raportti: 2025-02-19-Booking-System-Phase1-Report1.md

**Päivitys 5.3.2025**

ZAP raportti: 2025-02-19-Booking-System-Phase1-Report2.md