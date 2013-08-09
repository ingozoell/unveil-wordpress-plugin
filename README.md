## Unveil für WordPress ##

Immer mehr Studien zu Performance-Optimierung von Webseiten belegen die Wirksamkeit der sogenannten _Lazy Load_ Technik für Bilder: Der Geschwindigkeitsvorteil einer Webseite ergibt sich durch die reduzierte Menge an geladenen Grafiken. Beim Seitenaufruf werden nicht restlos alle Bilder vom Server angefordert und abgebildet, sondern nur die kleine Auswahl, die sich im Blickwinkel des Betrachters befindet. Bewegt sich der Leser innerhalb der Seite (= scrollt), lädt [Unveil.js](https://github.com/luis-almeida/unveil) benötigte Bilder dynamisch nach. Je nach Bildgröße ergibt sich für den Nutzer solch einer Seite nahezu kein visueller Unterschied bzw. bringt keinerlei Nachteile mit sich.

Nach der Inbetriebnahme des WordPress-Plugins laden Blogseiten deutlich schneller, da weniger Bytes durch die Leitung transferiert werden. Auch die Anzahl an parallelen (und beschränkten) Anfragen zum Server reduziert sich und beschleunigt den Ladevorgang zusätzlich.


### Video
Darstellung der Funktionsweise des Plugins [auf YouTube](http://www.youtube.com/watch?v=tMv5tl3Q4Aw). Beim Scrollen der Webseite (Fenster oben) werden Bilder automatisch geladen. Im unteren Fenster (Entwickler-Tools) werden entsprechend stattgefundene Requests abgebildet.


### Vorteile

- Das _Unveil WordPress-Plugin_ kann jederzeit gefahrlos aktiviert und deaktiviert werden, da an den Artikeln bzw. in der Blog-Datenbank keine Änderungen vorgenommen werden.
- Funktioniert mit jedem Caching-Plugin - auch mit [Cachify](http://cachify.de).
- Korrekte Funktionsweise der _Lazy Load_ Technik: Beim Aufruf der Blogseiten werden Bilder erst nach Bedarf nachgeladen und nicht wie bei zahlreichen anderen Lösungen erst komplett geladen und dann bei Bedarf angezeigt. Ein Traffic-lastiger und Performance-bedeutender Unterschied.
- Berücksichtigt werden alle im Artikel eingebundene Bilder inkl. Beitragsbild (Thumbnail).
- Keine Einstellungen vonnöten. Aktivieren, läuft.
- Schlicht und geschwind in der Ausführung.


### Beachtenswert
Das _Unveil WordPress-Plugin_ sollte mit jedem WordPress-konformen Theme fehlerfrei und auf Anhieb funktionieren. Dennoch einige wichtige Punkte aufgelistet:

- Es werden Bilder aus WordPress-Beiträgen berücksichtigt, die über die Mediathek eingefügt wurden und somit automatisch die CSS-Klasse _wp-image-*_ zugewiesen bekommen haben. Auf diese CSS-Klasse baut das komplette Plugin auf.
- Das Theme-Template _footer.php_ muss den WordPress-Funktionsaufruf _wp_footer()_ beinhalten. An dieser Stelle wird das erforderliche JavaScript geschrieben.
- Beim Seitenaufruf bekommen alle Beitragsbilder automatisch eine leere Grafik zugewiesen. Dies verhindert den ungewünschten Ladevorgang der Bildelemente im Browser. Das jQuery-Plugin _Unveil_ sorgt dafür, dass nur die sichtbaren Bilder vom Server geladen und angezeigt werden.
- Es ist davon auszugehen, dass Beitragsbilder von Google nicht länger indexiert werden können, da diese per Default nicht geladen werden.


### Inbetriebnahme

1. Obere Punkte beachten
2. Plugin downloaden (Download ZIP rechts in der Sidebar)
3. Ordner ins _plugins_ WordPress-Verzeichnis kopieren
4. _Unveil für WordPress_ aktivieren


### Formatierung

Optional können noch nicht geladene Bilder als Platzhalter via Theme-CSS dekoriert werden. Denkbar wäre ein punktierter Rahmen als eine Art visuelle Abgrenzung der Bilder. Auch ein Loader macht sich gut.

```css
img[src*='data:image/gif;base64'] {
	border: 1px dashed #dbdbdb;
}
```

```css
img[class*=wp-image-],
img[class*=wp-post-image] {
	background: url(/wp-includes/images/wpspin-2x.gif) no-repeat center center;
	background-size: 16px 16px;
}
```


## Autor
*Sergej Müller* / [Google+](https://plus.google.com/110569673423509816572?rel=author) / [Twitter](https://twitter.com/wpSEO) / [WordPress-Plugins](http://wpcoder.de)


### Todos

- Lösung für Nutzer ohne JavaScript
- Implementierung der HiDPI-Unterstützung


### Häufige Fragen

*Wie stelle ich sicher, dass das _Unveil WordPress-Plugin_ funktioniert?*<br />
In Entwickler-Tools des Browsers (Reiter _Netzwerk_ o.ä.) erkennt man wunderbar, dass Bilder erst beim Scrollen geladen werden. Siehe dazu auch das [Video](http://www.youtube.com/watch?v=tMv5tl3Q4Aw) mit dem Ladevorgang.



### Changelog

###### Version: 0.0.2
- Berücksichtigung der Beitragsbilder (Thumbnails)
- Beispiele für CSS-Formatierungen in der Doku

###### Version: 0.0.1
- _Unveil für WordPress_ geht online