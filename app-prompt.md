# Prompt für Binär-ASCII-Visualisierungs-App

## Projektbeschreibung
Erstelle eine interaktive Webanwendung zur Visualisierung von Binärzahlen und deren Interpretation als ASCII-Zeichen. Die App ist für den Einsatz am Smartboard in einer Unterrichtssituation konzipiert und soll Lernenden helfen, das Konzept von Bits, Bytes und deren verschiedene Interpretationen zu verstehen.

## Zielgruppe
- Schülerinnen und Schüler (Sekundarstufe)
- Lehrkräfte für Informatik/Digitale Bildung
- Einsatz am Smartboard/interaktiver Tafel

## Technische Anforderungen
- **Framework**: Vanilla HTML, CSS, JavaScript (für einfache Bereitstellung auf GitHub Pages)
- **Responsive Design**: Optimiert für große Bildschirme (Smartboard)
- **Touch-freundlich**: Große Buttons für Touch-Bedienung
- **Deployment**: GitHub Pages kompatibel
- **Browser-Kompatibilität**: Moderne Browser (Chrome, Firefox, Safari, Edge)

## Funktionale Anforderungen

### Kern-Interface
1. **8 Binär-Schalter (Hauptelement)**
   - 8 große, visuell ansprechende Toggle-Switches für je ein Bit
   - Jeder Schalter repräsentiert eine Binärstelle (von links nach rechts: 2^7 bis 2^0)
   - Klickbar/touchbar für Ein-/Ausschalten
   - Visuell klar unterscheidbar zwischen AN (1) und AUS (0)
   - Mindestgröße: 80px Höhe für Touch-Bedienung

2. **LED-Anzeigen über den Schaltern**
   - 8 "Lichter" direkt über jedem Schalter
   - Leuchten grün/hell wenn Bit = 1, dunkel/grau wenn Bit = 0
   - Verstärken die physische Schalter-Metapher

3. **ASCII-Ausgabe (rechts)**
   - Großer Anzeigebereich für den entsprechenden ASCII-Buchstaben
   - Schriftgröße: mindestens 120px für Sichtbarkeit am Smartboard
   - Zeigt das Zeichen an, das dem aktuellen Byte-Wert entspricht
   - Behandlung von nicht-druckbaren Zeichen (0-31, 127): Anzeige als "[Steuerzeichen]" oder ähnlich

### Modulare Erweiterungen (Ein-/Ausschaltbar)

4. **Modul: Dezimalwerte unter Schaltern**
   - Aktivierbar über Checkbox/Button
   - Zeigt unter jedem Schalter den entsprechenden Dezimalwert (128, 64, 32, 16, 8, 4, 2, 1)
   - Hilft beim Verständnis der Stellenwerte

5. **Modul: Zweierpotenzen**
   - Aktivierbar über Checkbox/Button
   - Zeigt 2^7, 2^6, 2^5, ... 2^1, 2^0 unter den entsprechenden Schaltern
   - Verdeutlicht das Potenz-System

6. **Modul: Binärzahl-Anzeige**
   - Zeigt die aktuelle 8-Bit-Binärzahl als String (z.B. "01000001")
   - Große, gut lesbare Schrift

7. **Modul: Dezimal-Ausgabe**
   - Zeigt den Dezimalwert des aktuellen Bytes (0-255)
   - Große Anzeige neben der ASCII-Ausgabe

8. **Modul: Graustufen-Visualisierung**
   - Zeigt ein Quadrat/Rechteck, das den aktuellen Byte-Wert als Graustufe darstellt
   - Wert 0 = Schwarz, Wert 255 = Weiß
   - Verdeutlicht alternative Interpretation derselben Bits

### Erweiterte Features

9. **Preset-Buttons**
   - "Reset" (alle Bits auf 0)
   - "Beispiel A" (setzt Bits für ASCII 'A' = 65 = 01000001)
   - "Beispiel Z" (setzt Bits für ASCII 'Z' = 90 = 01011010)
   - "Maximum" (alle Bits auf 1 = 255)

10. **Schnell-Eingabe**
    - Eingabefeld für Dezimalzahl (0-255) mit "Setzen"-Button
    - Eingabefeld für ASCII-Zeichen mit "Setzen"-Button
    - Konvertiert automatisch und setzt die entsprechenden Bits

## Design-Anforderungen

### Layout
- **Hauptbereich**: 8 Schalter horizontal angeordnet, zentriert
- **LEDs**: Direkt über den Schaltern
- **ASCII-Ausgabe**: Rechts neben den Schaltern, prominent platziert
- **Module**: Unter den Schaltern, in Boxen/Panels organisiert
- **Steuerung**: Modulare Aktivierung über Buttons/Checkboxes am oberen oder seitlichen Rand

### Farbschema
- **Hintergrund**: Helles, neutrales Design (weiß/hellgrau)
- **Schalter AUS**: Grau/dunkel
- **Schalter AN**: Grün oder blau (deutlich unterscheidbar)
- **LEDs AUS**: Dunkelgrau
- **LEDs AN**: Helles Grün oder Gelb
- **Text**: Dunkle Farben für gute Kontraste
- **Module**: Leicht abgesetzt durch Rahmen oder Hintergrundfarbe

### Typografie
- **Schriftart**: Sans-serif, gut lesbar (z.B. Arial, Helvetica)
- **ASCII-Ausgabe**: 120px+ für Smartboard-Sichtbarkeit
- **Dezimalwerte**: 18px+ unter Schaltern
- **Beschriftungen**: 16px+ für Module und Labels

## Technische Implementierung

### HTML-Struktur
```html
<!DOCTYPE html>
<html>
<head>
    <title>Binär-ASCII-Visualizer</title>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
</head>
<body>
    <div class="container">
        <header>
            <h1>Binär-ASCII-Visualizer</h1>
            <div class="module-controls">
                <!-- Checkboxes für Module -->
            </div>
        </header>
        
        <main>
            <div class="bit-display">
                <div class="leds">
                    <!-- 8 LED-Anzeigen -->
                </div>
                <div class="switches">
                    <!-- 8 Toggle-Switches -->
                </div>
                <div class="decimal-values" id="decimal-module">
                    <!-- Dezimalwerte unter Schaltern -->
                </div>
                <div class="power-values" id="power-module">
                    <!-- Zweierpotenzen unter Schaltern -->
                </div>
            </div>
            
            <div class="output-area">
                <div class="ascii-output">
                    <!-- ASCII-Zeichen-Anzeige -->
                </div>
                <div class="decimal-output" id="decimal-output-module">
                    <!-- Dezimalwert-Anzeige -->
                </div>
                <div class="binary-output" id="binary-module">
                    <!-- Binärzahl-Anzeige -->
                </div>
                <div class="grayscale-output" id="grayscale-module">
                    <!-- Graustufen-Quadrat -->
                </div>
            </div>
        </main>
        
        <footer>
            <div class="presets">
                <!-- Preset-Buttons -->
            </div>
            <div class="quick-input">
                <!-- Schnell-Eingabe -->
            </div>
        </footer>
    </div>
</body>
</html>
```

### CSS-Anforderungen
- **Flexbox/Grid** für responsive Layout
- **CSS-Variablen** für einheitliche Farbgebung
- **Hover-Effekte** für interaktive Elemente
- **Transitions** für sanfte Animationen beim Schalten
- **Media Queries** für verschiedene Bildschirmgrößen
- **Touch-optimierte Größen** (min. 44px Touch-Targets)

### JavaScript-Funktionalität
- **Event-Listener** für alle Schalter
- **Bitweise Operationen** für Berechnungen
- **Modulare Funktionen** für jede Interpretation (ASCII, Dezimal, etc.)
- **State Management** für aktive Module
- **Validierung** für Eingaben
- **ASCII-Tabelle** für Zeichenkonvertierung

## Spezielle Anforderungen für den Unterrichtseinsatz

### Pädagogische Überlegungen
1. **Schrittweise Komplexität**: Module können einzeln aktiviert werden, um Überforderung zu vermeiden
2. **Immediate Feedback**: Alle Änderungen werden sofort in allen aktiven Modulen sichtbar
3. **Große Schrift und Buttons**: Optimiert für Smartboard-Nutzung
4. **Klare Beschriftungen**: Deutsche Beschriftungen für bessere Verständlichkeit

### Barrierefreiheit
- **Kontrastreiche Farben** für gute Lesbarkeit
- **Große Touch-Targets** für einfache Bedienung
- **Klare visuelle Hierarchie**
- **Alt-Texte** für alle interaktiven Elemente

### Performance
- **Schnelle Reaktionszeit** bei Schalter-Betätigung
- **Lightweight**: Keine externen Abhängigkeiten
- **Offline-fähig** nach dem ersten Laden

## Deployment-Hinweise
- Alle Dateien in einem GitHub Repository
- GitHub Pages Aktivierung über Repository Settings
- Einfache Ordnerstruktur: index.html, style.css, script.js
- README.md mit Nutzungsanleitung für Lehrkräfte

## Erweiterungsmöglichkeiten für die Zukunft
- Hexadezimal-Anzeige
- Verschiedene Zeichensätze (UTF-8, etc.)
- Sound-Effekte für Schalter-Betätigung
- Animations-Modi für Demonstrationszwecke
- Export-Funktion für Screenshots
- Mehrsprachigkeit (English/Deutsch toggle)

Diese App soll das zentrale Werkzeug für Phase 3 des Unterrichts sein und den Schülerinnen und Schülern helfen, die abstrakte Verbindung zwischen Bits, Bytes und deren verschiedenen Interpretationen zu verstehen.
