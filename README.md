

### Was macht dieses Script?

Dieses Script wurde in Node-RED entwickelt und steuert einen Lüfter basierend auf verschiedenen Umweltbedingungen, die von Sensoren erfasst werden. Ziel ist es, die Lüftersteuerung automatisch und effizient zu gestalten, um optimale Innenraumluftbedingungen zu gewährleisten. Die Funktion erfasst Temperatur- und Feuchtigkeitsdaten sowohl von Innen- als auch Außensensoren und berechnet die Taupunkte, um die Lüftungsentscheidung zu treffen.

### Funktionsweise:

Die Funktion wertet die folgenden Parameter aus:

1. **Innere Temperatur (`temperature_C`):** Die aktuelle Temperatur im Innenraum.
2. **Innere Luftfeuchtigkeit (`humidity`):** Die gemessene Luftfeuchtigkeit im Innenraum.
3. **Außentemperatur (`temperature_C`):** Die aktuelle Temperatur im Außenbereich.
4. **Außenluftfeuchtigkeit (`humidity`):** Die gemessene Luftfeuchtigkeit im Außenbereich.

### Bedingungen für die Lüftersteuerung:

Der Lüfter wird nur dann eingeschaltet, wenn folgende Bedingungen erfüllt sind:

1. **Innentemperatur über 15 °C:** Damit wird sichergestellt, dass keine kühle Luft ins Innere gelangt, wenn es drinnen zu kalt ist.
   
2. **Luftfeuchtigkeit innen mindestens 60 %:** Dies verhindert das Einschalten des Lüfters, wenn die Luftfeuchtigkeit im Innenraum bereits niedrig genug ist.

3. **Taupunkt außen mindestens 3 °C niedriger als innen:** Der Lüfter wird nur aktiviert, wenn die Feuchtigkeit der Außenluft erheblich trockener ist als die Innenluft, was das Eindringen von Feuchtigkeit in den Innenraum vermeidet.

### Entscheidungsprozess:

- **Taupunktberechnung:** Die Funktion berechnet die Taupunkte für Innen- und Außenbedingungen, um das Feuchtigkeitsverhältnis korrekt zu bewerten.
- **Bedingungsprüfung:** Die oben genannten Bedingungen werden einzeln überprüft. Debugging-Nachrichten helfen, die Entscheidungsprozesse transparent zu machen und sicherzustellen, dass jede Bedingung korrekt ausgewertet wird.
- **Lüftersteuerung:** Der Lüfter wird nur dann aktiviert, wenn **alle** Bedingungen erfüllt sind. Andernfalls bleibt er ausgeschaltet.

### Warum diese Bedingungen?

Durch diese spezifischen Bedingungen soll vermieden werden, dass der Lüfter die Luftqualität im Innenraum verschlechtert. Die Steuerung hilft, Energie zu sparen und den Komfort im Innenraum zu verbessern, indem nur unter optimalen Bedingungen gelüftet wird.

---

Mit diesem Script schaffe ich eine dynamische und automatische Steuerung des Lüfters, die genau auf die aktuellen Innen- und Außenbedingungen abgestimmt ist, um das Raumklima effizient zu regulieren.
