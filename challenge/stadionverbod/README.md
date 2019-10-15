# Challenge

`Hoe kunnen we mensen met een stadionverbod uit de voetbalstadions houden ?`

## Oplossing

Technisch vrij eenvoudig, gezien FOD BOSA DG DT als dienstenintegrator reeds componenten heeft om dit te implementeren.

- [FSB](https://dtservices.bosa.be/nl/services/fsb/catalogue) webservices om op een beveiligde manier data uit te wisselen met andere overheidsdiensten
- [CSAM](https://csam.be/nl/over-csam.html) om toegang tot een applicatie te beheren (via beveiligde manier om aan te melden + beheer rollen: wie mag wat)

Juridisch kan er wel een bijkomende moeilijkheid zijn, hoewel dit ook voor de huidige gang van zaken zal zijn: wie mag de identiteit controleren (stewards ? enkel politie ?)

## Componenten

### Beveiligde invoer applicatie (politie)

In plaats van het versturen van Excels, kunnen bevoegde personen (federale / lokale politie ?) een online database invullen.
Zij moeten hiervoor met hun eID-kaart aanmelden via de standaard-component CSAM, en na controle mogen de personen deze database verder aanvullen.

Bijvoorbeeld met de volgende gegevens:
- rijksregisternummer van de persoon
- voornaam en naam van de persoon
- start- en einddatum van het verbod
- type verbod / plaats (vb: enkel voetbalvelden of ook andere locaties, enkel bepaalde stad of niet)

### Beveiligde controle applicatie (ingang stadion)

Bij de ingang moet de steward / politieman aanmelden op de online applicatie, met de rol van controleur.
Deze rol heeft geen rechtstreekse toegang tot de database, en kan ook geen gegevens aanpassen, maar kan enkel via de applicatie een webservice gebruiken.
Deze webservice geeft als antwoord enkel "JA" of "NEE" (geen toegang) terug op basis van een rijksregisternummer.

Dit rijksregisternummer kan ingelezen worden via de eID-kaart:
- via de chip door de eID-kaart in de kaartlezer te steken
- of door de barcode op de achterkant van de eID-kaart te scannen.

Indien de persoon geen toegang heeft, kan er een rood scherm getoond worden en/of meteen de veiligheidsdiensten verwittigd worden.

### Voordelen / nadelen

Het voordeel van deze aanpak is dat enkel het minimum aan persoonsgebonden informatie uitgewisseld wordt, en dat er ook bijgehouden wordt wie, wanneer en waar gecontroleerd werd.

Nadeel is dat er dan in elk stadium ook op voldoende plaatsen aan de ingang internettoegang (al dan niet via WiFi of netwerkkabels) moet zijn, en dat de applicatie dan ook gegarandeerd beschikbaar moet zijn op wedstrijddagen ("Service Level Agreement")

## Aandachtspunten

- Wat met personen zonder Belgische identiteitskaart ? Mogelijk paspoort of buitenlandse eID kaart.
- Beveiliging is maar zo sterk als de zwakste schakel: controle identiteitskaart werkt niet als er bijvoorbeeld over een muur geklommen kan worden...

