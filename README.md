## Aufgabe 03 - Routing und Fehlerbehandlung

In der ersten Aufgabe haben wir gesehen, dass es Anfragen wie `GET` und `POST` gibt, die bestimmen, was die Funktion des Endpunktes ist. (Abfragen, Erstellen in unserem Fall)
Jetzt wollen wir uns `PUT` und `DELETE` anschauen.

* `PUT` aktualisiert eine Ressource, die es schon gibt.
* `DELETE` löscht eine existierende Ressource.

Nachdem wir die obigen Anfragen für unseren Musikladen eingeführt haben, werden wir uns Fehlerbehandlung anschauen.
Was ist, wenn was schief geht, während eine Anfrage bearbeitet wird?
Wir wollen den User (bzw. das Programm, das unsere API benutzt) wissen lassen, was schief ging auf konsistente Art. Wir erreichen so eine Fehlerbehandlung, indem wir Middleware-Funktionen schreiben, die sich um Fehlerbehandlung kümmern.

**Hintergrund**:
Unser Kunde, der Musikladen, möchte gern Produkte aktualisieren und aus dem Angebot löschen können. Neben den Produkt-Datenmodell, möchte unser Kunde zwei weitere Datenmodelle bekommen. Eins für Nutzer (users) und eins für Bestellungen (orders)

**Die Schritte**:

1. Erstelle drei weitere Endpunkte (Routen) für das Produkt-Datenmodell (record)

   - `records/:id` -> eine `GET`-Anfrage, die ein Produkt anhand der übergebenen `id` liefert
   - `records/:id` -> eine `PUT`-Anfrage, die anhand einer `id` ein Produkt aktualisiert
   - `records/:id` -> eine `DELETE`-Anfrage, die das Produkt mit der `id` löscht

2. Erstelle neue Endpunkte für Nutzer (`users`) und Bestellungen (`orders`). 

    Ein Nutzer enthält eine ID, Vor-, Nachname, Email und Passwort. (first name, last name, email, password). 
    Eine Bestellung enthält eine Produkt-Id (id) und eine Anzahl (quantity).
    Später fügen wir den Modellen weitere Eigenschaften hinzu.

    Nutzer Modell (users)
    - `users` -> `GET` alle Nutzer ausgeben
    - `users/:id` -> `GET` ein bestimmter Nutzer ausgeben
    - `users` -> `POST` einen Nutzer erstellen
    - `users/:id` -> `PUT` einen Nutzer aktualisieren
    - `users/:id` -> `DELETE` einen Nutzer löschen

    Bestellungen Modell (orders)
    - `orders` -> `GET` alle Bestellungen ausgeben
    - `orders/:id` -> `GET` eine Bestellung ausgeben
    - `orders` -> `POST` eine Bestellung anlegen
    - `orders/:id` -> `PUT` eine Bestellung aktualisieren
    - `orders/:id` -> `DELETE` eine Bestellung löschen 

3. Wenn diese Endpunkte alle funktionieren und unsere Datenbank richtig aktualisieren, wird es Zeit eine Middleware-Funktion zu erstellen, die mit möglichen Fehlern umgeht.

- Sucht die passenden Fehler-Codes aus: https://de.wikipedia.org/wiki/HTTP-Statuscode#Liste_der_HTTP-Statuscodes

https://developer.mozilla.org/en-US/docs/Web/HTTP/Status

