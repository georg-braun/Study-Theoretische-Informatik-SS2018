# Theoretische Informatik
## Praktikumsaufgaben im Rahmen des Modul Theoretische Informatik im SS18

- [x] Entwicklung eines Parsers für WHILE0-Programme (Lexikalische- und Syntaktische-Analyse)
- [ ] Compiler nach URM

### Benötigte Software
- Java
- Javac (im JDK enthalten)
- JavaCC
### Optionale Software
- Eclipse
- Eclipse JavaCC Plugin

### Einrichtung der Software
- Die Pfade zu den einzelnen Anwendungen (java, javac und javacc) zu der Umgebungsvariable PATH hinzufügen. (Erleichtert die spätere Verwendung)
- Die Entwicklung mit dem JavaCC Plugin in Eclipse ist sehr hilfreich. Eine Anleitung welche die Verwendung sehr gut beschreibt ist unter folgendem Link zu finden: http://homepages.gac.edu/~hvidsten/courses/MC270/Labs/project4-GacApplication/project-files/JavaCC/JavaCC-Eclipse.html

### Verwendung
Im Link der obigen Anleitung wird auch die Nutzung von JavaCC im Rahmen von Eclipse erklärt.
Die Verwendung von Eclipse ist aber nicht zwangsläufig notwendig. Alternativ lässt sich dies auch über die Kommandozeile (Aufruf der einzelnen Programme) wie folgt realisieren:

Angenommen die Grammatik ist in der Datei `WhileNullGrammar.jj` enthalten. Die Ausführung von `javacc WhileNullGrammar.jj` startet den Parsergenerator. Daraus resultieren `.java` Dateien mit dem Quellcode. Diese können dann mit `javac WhileNullParser.java` kompiliert werden (Notiz: Die Datei heißt nun WhileNullParser, da dies dem genutzten Klassennammen in der Grammatikdefinition entspricht. Nach dem Kompilieren sind die `.class` Dateien vorhanden. Mit dem Aufruf `java WhileNullParser` (ohne Dateiendung!) wird der Parser ausgeführt. Je nach Implementation können noch weitere Argumente übergeben werden.

Insgesamt entsteht folgende Abfolge von Befehlen.
Dabei wird der zu überprüfende Text in der Datei ex.txt verwaltet.
```
// Erzeugung des Parsers
javacc WhileNullGrammar.jj
javac WhileNullParser.java

// Ausführen des Parsers mit der Datei als Argument
java WhileNullParser ex.xt
```

Hier auch mal ein konkretes Beispiel.

Die Datei ex.txt enthält:
```
PROG(in X1; out Y);
var(H1, H2, H3, H4, H5, H6);
H5 = H5 + 1;
while H2 != X1 do begin
H2 = H2 + 1;
while H3 != X1 do begin
H3 = H3 + 1;
H1 = H1 + 1
end;
H3 = 0 end
```
Erzeugen und Ausführen des Parsers
```
PS E:\Studentenprojekte\TheoretischeInformatik\Praktikum\bin> javacc WhileNullGrammar.jj
Java Compiler Compiler Version 5.0 (Parser Generator)
(type "javacc" with no arguments for help)
Reading from file WhileNullGrammar.jj . . .
File "TokenMgrError.java" does not exist.  Will create one.
File "ParseException.java" does not exist.  Will create one.
File "Token.java" does not exist.  Will create one.
File "SimpleCharStream.java" does not exist.  Will create one.
Parser generated successfully.
PS E:\Studentenprojekte\TheoretischeInformatik\Praktikum\bin> javac WhileNullParser.java
PS E:\Studentenprojekte\TheoretischeInformatik\Praktikum\bin> java WhileNullParser ex.txt
ExampleParser: Reading the file ex.txt ...
Gültig
```
