# Kaarten

Volgens het [sjabloon afspraken](https://provincies.incijfers.be/databank/report/?id=sjabloon_grafiekstijl) gebruiken we voor kaarten en grafieken op volle breedte een breedte van **750** pixels.

Geef je enkel een breedte op en geen hoogte, dan krijgt je kaart de standaardbeeldverhouding van **4:3**. Bij een breedte van 750 is de hoogte dus **562** (afgerond). Let op: de opgegeven afmetingen hebben altijd betrekking op de complete figuur, d.w.z. de eigenlijke kaart of grafiek + de legende + de bronvermelding + een witrand rondom.

Deze standaardbeeldverhouding is oké voor kaartjes van alle provincies behalve voor Vlaams-Brabant, omdat die provincie eerder langgerekt van vorm is. Daarom kunnen we voor Vlaams-Brabant beter een kleinere hoogte opgeven, namelijk **450** (de beeldverhouding is dan **5:3**). Ook bij een kaart van het Vlaams Gewest gebruiken we beter een hoogte van 450.

Onderstaande code komt uit hoofdstuk 1 van de omgevingsanalyse en laat zien hoe je dit kunt programmeren – plaats deze code bovenaan het rapport, bij de voorbereiding voor de (eerste) kaart:

```
kaart_hoogte = 562 /* standaard kaarthoogte bij een breedte van 750 (beeldverhouding 4:3) */
if Equal(Code(Level(Item(input_geo,0))), "provincie") then
	if Equal(Item(input_geo,0), provincie._20001) then
		kaart_hoogte = 450 /* kleinere kaarthoogte voor Vlaams-Brabant (beeldverhouding 5:3) */
	end if
else
	if Equal(Item(input_compare,0), provincie._20001) or Equal(Item(input_compare,0), gewest._2000) then
		kaart_hoogte = 450 /* kleinere kaarthoogte voor Vlaams-Brabant of het Vlaams Gewest (beeldverhouding 5:3) */
	end if
end if

```

N.B.: wanneer het rapport wordt opgevraagd voor een provincie, dan wordt een kaart van de provincie getoond; wordt het rapport opgevraagd voor een gemeente, dan wordt een kaart van het eerste vergelijkingsgebied getoond. Dat kan de provincie of het gewest zijn.

De kaart wordt in de tekst op de gewenste plaats ingevoegd met volgende code:

```
showInteractive(Kaart_1_1,750,kaart_hoogte)
```

Dit zal ofwel een langgerekte kaart laten zien (met beeldverhouding 5:3) voor het Vlaams Gewest of voor Vlaams-Brabant, of een hogere kaart (met beeldverhouding 4:3) voor de andere provincies.

Voorbeeld 1: kaart van Oost-Vlaanderen

![kaart_ovl](https://user-images.githubusercontent.com/101627698/226315322-e6af8de3-0f80-4eaa-8b40-6ab22145f262.png)

Voorbeeld 2: kaart van het Vlaams Gewest

![kaart_vl](https://user-images.githubusercontent.com/101627698/226316805-c76bfb51-1865-4d03-ae8d-79151a80b773.png)

