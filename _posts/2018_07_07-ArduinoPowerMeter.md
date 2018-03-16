---
published: false
---
# wie kann man mit einem Arduino den Verlauf der Netzspannung messen?
Dazu gibts es verschiedene Ansätze. Einer der einfachsten Ansätze ist die verwendung eines Transformators und die anschliessende Anpassung der Ausgangsspannung an die Eingangsspannungsbereich des Arduino-ADC (0..5V)

Ein Beispiel dafür, wie man das machen kann, findet man unter
https://learn.openenergymonitor.org/electricity-monitoring/voltage-sensing/measuring-voltage-with-an-acac-power-adapter.

Es existiert auch eine verbesserte Variante der Schaltung unter https://learn.openenergymonitor.org/electricity-monitoring/ctac/acac-buffered-voltage-bias

Zu beachten ist, dass ein Transformator eine lastabhängige pahsenverschiebung zwischen Primaer- und Sekundaerseite hat. Diese Phasenverschiebung kann man z.B. mit einem Oszi messen, welches auf die Netzspannung synchronisieren kann. Alternativ nimmt man Transformatoren, die von openenergymonitor bereits vermessen wurden.


