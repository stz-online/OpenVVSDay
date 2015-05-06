# OpenVVSDay

Repository mit Datensammlung zum Open VVS Day

alle Informationen unter http://www.stuttgarter-zeitung.de/openvvs

## Pad
Zum Austausch bezüglich Fragen, Themenideen etc. haben wir [ein Pad eingerichtet] (https://openvvsday.titanpad.com/1)

## Materialsammlung

Wir haben hier einige Anwendungen und Quellen mit Lektüre für Einsteiger_innen wie Fortgeschrittene zusammengefasst.

### Allgemein

Einen kleinen Einstieg, welche Daten im ÖPNV überhaupt anfallen und wie sie verarbeitet werden, bieten die ersten Kapitel [der Diplomarbeit von Stefan Kaufmann](http://dbis.eprints.uni-ulm.de/1054/). Auch auf [travel-api](http://www.travel-api.com/resources.html) finden sich einige Beispiele, was alles mit offenen Transitdaten möglich ist.

Der VVS stellt folgende Datenquellen bereit:

 * **GTFS:** Statischer *Soll*fahrplan, d.h. wie sollte der Nahverkehr laufen, wenn er vollkommen nach Plan läuft (so wie im gedruckten Fahrplan, aber durch und durch maschinenles- und auswertbar)
 * **EFA:** Die Elektronische Fahrplanauskunft, bekannt durch die VVS-App und -website. Weniger bekannt dürfte sein, dass sie auch eine XML-Schnittstelle hat. Echtzeitdaten (Verspätungen etc.) kann sie auch, aber eben immer nur abfragebasiert.
 * **TRIAS:** Auch eine echtzeitfähige Auskunft, basierend auf einem [Standard des VDV](https://www.vdv.de/ip-kom-oev.aspx). Ebenfalls abfragebasiert.

### GTFS

Ein viel verwendetes Datenformat, das auch für den Open-VVS-Day vom VVS zur Verfügung gestellt wird, ist **GTFS** [(Wikipedia)](http://en.wikipedia.org/wiki/General_Transit_Feed_Specification). Die [ausführliche Spezifikation](https://developers.google.com/transit/gtfs/reference) beschreibt das Format bis in die Tiefe; für einen kurzen Überblick reicht in der Regel aber auch [diese Übersicht von openplans.](http://blog.openplans.org/2012/08/the-openplans-guide-to-gtfs-data/)

Eine relativ aktuelle Übersicht über das Format und mögliche Anwendungen [bietet dieses Slidedeck](https://prezi.com/p3s0p6tkg0uf/the-many-uses-of-gtfs-data-apta-transitech-march-2013/).

Wesentlicher Punkt ist: GTFS ist der *komplette* Fahrplan, d.h. egal welche Analyse gemacht werden soll – solange das der Fahrplan her gibt, geht das. Von A nach Z und zwischendurch mit dem Fahrrad von Haltestelle zu Haltestelle radeln oder einen Döner auf dem Weg kaufen? Geht schon, $irgendwie. Beispielsweise [Erreichbarkeitsanalysen wie die von Mapnificent](https://stefanw.github.io/mapnificent/).

### EFA

Die [Elektronische Fahrplanauskunft (EFA)](https://de.wikipedia.org/wiki/Elektronische_Fahrplanauskunft_(Software)) ist das Stück Software, das euch eine Routenplanung im VVS-Netz ausspuckt. EFA hat auch eine XML-Schnittstelle – über den [Public Transport Enabler](https://github.com/schildbach/public-transport-enabler) ist das die Quelle, die Öffi mit den jeweiligen Verbunddaten füttert.

Die meisten EFA-Instanzen von Verbünden tauschen untereinander Daten aus, so dass die VVS-EFA z.B. auch Fahrplanauskünfte in Essen oder Ulm geben kann. In der Regel liegen die Echtzeitdaten (Verspätungsmeldungen etc.) aber immer nur für den „Heimatverbund“ vor – d.h. die Verspätungen Stuttgarter Busse und Bahnen tauchen zwar in der VVS-EFA auf, aber nicht z.B. in der DING-EFA. Umgekehrt gilt das dann genauso für Busse in Ulm.

Eine Dokumentation zur EFA-Schnittstelle gibt es von der [Linz Linien AG](http://data.linz.gv.at/katalog/linz_ag/linz_ag_linien/fahrplan/LINZ_AG_Linien_Schnitstelle_EFA_v7_Echtzeit.pdf); die Funktionalität ist quasi direkt übertragbar.

 * API-Endpunkt für Verbindungsauskünfte (A nach B): http://efastatic.vvs.de/OpenVVSDay/XML_TRIP_REQUEST2?language=de
 * API-Endpunkt für Abfahrtstafelauskünfte (Haltestelle C): http://efastatic.vvs.de/OpenVVSDay/XML_DM_REQUEST?

 * Beispielabfrage für die Haltestellentafel am Charlottenplatz: http://efastatic.vvs.de/OpenVVSDay/XML_DM_REQUEST?laguage=de&typeInfo_dm=stopID&nameInfo_dm=Charlottenplatz&deleteAssignedStops_dm=1&useRealtime=1&mode=direct

Neben dem Public Transit Enabler gibt es EFA-Bibliotheken auch in anderen Sprachen – [beispielsweise in Perl](http://finalrewind.org/projects/Travel-Routing-DE-VRR/), hier muss nur der EFA-Endpunkt vom VRR auf den VVS umgestellt werden.

Wichtig ist bei der EFA: Die EFA gibt aus, was die EFA für richtig hält. Und nichts anderes. Spezialanforderungen (zwischendurch Döner kaufen) sind nicht ohne weiteres möglich. Hier geht es nur von A nach B.

### Sonstige Datenquellen

Interessant werden Anwendungen ja vor allem auch dann, wenn sie mit anderen Daten verschnitten werden. Die Daten der OpenStreetMap lassen sich beispielsweise sehr gut per [Overpass API](http://wiki.openstreetmap.org/wiki/Overpass_API) abfragen – eine schnelle Variante zum Zusammenklicken von Abfragen ist [Overpass Turbo](http://overpass-turbo.eu/).

----

**Changelog**

 * 2015-04-22: Erste Fassung (stz)
 * 2015-04-27: Text in Fließtext gebracht und Links angereichert (stk)
