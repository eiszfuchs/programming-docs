# Generators / Iterables

So, erstes Thema war für @DaxPhon und ist über Function Generators / Iterables. Das ist interessant für PHP/Python/ES6 und die Hochsprachen. Ich versuche das über den Tag irgendwie immer mal wieder weiter zu erklären. Ggf. in der Pause. Ich setze dafür voraus, dass Ihr wisst, was eine Funktion ist und dass Ihr schon mal was von "for"/"foreach" gehört habt.

Ansonsten konsumiert das einfach und es wird später alles viel klarer werden.

Das ist jetzt Advanced-Level.

Iterables sind Objekte, die ein Iterable-Interface implementieren.
Interfaces sind wie Blaupausen, mit denen man festlegen kann, welche Methoden und Eigenschaften eine Klasse definieren muss. Diese Blaupausen implementieren selber nichts, sondern legen nur die Signatur der Klassen-Mitglieder (Class members) fest.

Je nach Sprache ist das Iterable-Interface ein bisschen anders definiert und mehr oder weniger Magic, aber alles kommt zusammen zu:
Ein Iterable ist eine Klasse, die eine bestimmte Methode anbietet, mit der ein einzelner [nächster] Wert geliefert wird.

Ein typisches Iterable ist ein Array.

Wenn Ihr also jetzt zum Beispiel in PHP einen Array [1, 2, 3, 4, 5, 6, 7, 8] erzeugt und über den drüber iteriert, dann ruft das intern auf diesem Array eine GibMirDasNächsteDings-Methode auf. Beim ersten Aufruf liefert der Array also 1, beim nächsten 2, usw.
Dieser Wert ist dann in der for-Schleife verfügbar.

Wenn der Array jetzt 8 geliefert hat, versucht die Schleife, noch einen Wert mehr zu holen, aber der Array sagt dann einfach "nö, mehr gibt's nicht, du gierschlund", und die for-Schleife bricht ab.

So funktioniert ein Iterable im Groben.

Function generators sind ziemlich coole Teile. Die sind sowas wie Iterators, aber cooler. Stellt es Euch wie Funktionen vor, die ein Gedächtnis haben und mehrere Werte liefern können statt nur einen einzigen.

Man fragt also auch einfach so lange Werte an, bis die Funktion/der Generator keinen Bock mehr hat, noch einen Wert zu liefern.

Das praktische ist, dass man das nicht zwingend in einem for(each) machen muss. Aber man könnte.

Sagen wir, ihr wollt über eine sehr große Anzahl von Zahlen iterieren. Einen Array mit allen Zahlen zwischen 0 und 1000000000 zu erzeugen würde unglaublich viel Speicher fressen und Euer Programm ggf. zum Absturz bringen.

Stattdessen würdet Ihr wohl eher einen Function generator oder ein Iterable schreiben, das einfach intern hochzählt und eine Zahl nach der nächsten liefert.

Man kann das ganze Prinzip auch Streamen nennen.

Das wird besonders praktisch, wenn Ihr Euren eigenen Wrapper für z.B. Datenbank-Querys baut, der nicht alle Ergebnisse auf einmal in den RAM pumpen sollte, sondern jede Zeile einzeln.

Diesen "Zwischenwert" eines Generators liefert man - je nach Sprache und Implementierung - mit dem Keyword "yield".

## Mehr zum Thema

### PHP

[Generators in PHP](http://php.net/manual/en/language.generators.overview.php)

### Ruby

[Generators in Ruby](http://patshaughnessy.net/2013/4/3/ruby-2-0-works-hard-so-you-can-be-lazy)

### Javascript

[Generators in ES6](https://developer.mozilla.org/de/docs/Web/JavaScript/Reference/Statements/function*)

(Wenn Ihr Chrome nicht zum nächsten Internet Explorer machen wollt, seht davon ab, Generators jetzt schon produktiv einzusetzen.)

### Python

[Generators und Iterables in Python](https://wiki.python.org/moin/Generators)

Hier sei übrigens noch am Rande erwähnt, dass das Konstrukt

```javascript
    for (var i = 0; i < 10; i += 1)
```

in Python nicht existiert, weil Python einfach über eine Liste von Ziffern iteriert, die von einem Generator erzeugt wird.
