---
published: false
---
# wie kann man mit einem Arduino den Verlauf der Netzspannung messen?
Dazu gibts es verschiedene Ansätze. Einer der einfachsten Ansätze ist die verwendung eines Transformators und die anschliessende Anpassung der Ausgangsspannung an die Eingangsspannungsbereich des Arduino-ADC (0..5V)

Ein Beispiel dafür, wie man das machen kann, findet man unter
https://learn.openenergymonitor.org/electricity-monitoring/voltage-sensing/measuring-voltage-with-an-acac-power-adapter.

Es existiert auch eine verbesserte Variante der Schaltung unter https://learn.openenergymonitor.org/electricity-monitoring/ctac/acac-buffered-voltage-bias

Zu beachten ist, dass ein Transformator eine lastabhängige pahsenverschiebung zwischen Primaer- und Sekundaerseite hat. Diese Phasenverschiebung kann man z.B. mit einem Oszi messen, welches auf die Netzspannung synchronisieren kann. Alternativ nimmt man Transformatoren, die von openenergymonitor bereits vermessen wurden.

# PoC mit einem Printtrafos aus der Bastelkiste
Der Verlauf der Ausgangsspannung mehrerer Printtrafos aus der Bastelkiste wird mit einem CRO aufgenommen. Im Line-Triggermodus des CRO wird anschliessend der Phasenwinkel der Spannung zwischen der Primär- und der Sekundärseite bestimmt.

| Trafo           | U_sek laut Aufdruck  |U_sek Leerlauf   | Phasenwinkel Leerlauf |
| --------------- |:--------------------:|:---------------:|:---------------------:|
| Marschner 13203 | 15 V                 | 26 V            | 21.6 °                |
| VEB GBB         | 20 V                 |           | |

Dieser recht hohe Phasenwinkel geht gemäß einer Internetrecherche (https://www.mikrocontroller.net/topic/100110#869046) auf die Reihenschaltung des Wicklungswiderstandes mit der Hauptinduktivität zurück, soll für Kleinleistungstrafos typisch sein und mit zunehmender Belastung deutlich zurück gehen. Bei einem bestimmten Lastverhältnis soll es sogar zu einer kompletten Kompensation der Phasenverschiebung kommen.

# PoC des sekundärseitigen Spannungsphasenwinkels eines Printtrafos in Anhängigkeit von der Last
Der verwendete Printtrafo liefert laut Aufdruck einen Sekundärseitigen Strom von 215 mA bei einer Spannung (Effektivwert) von 15 V. Mit R=U/I ergibt sich für diesen Arbeitspunkt ein ohmscher Widerstand von rund 69.8 Ohm. Die dabei umgesetzte Leistung errechnet sich mit P=U*I zu rund 3.3 Watt




