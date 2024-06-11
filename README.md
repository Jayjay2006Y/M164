# M164

## Aufgaben Recap Fragen Kellenberger


1. Daten, Informationen, Wissen. Beispiel: Wechselkurs beträgt 0,89 EUR für 1 USD".
2. Durch Entitäten und ihre Beziehungen im logischen Modell.
3. Anomalien sind Fehler in Daten. Arten: Einfüge-, Löschungs-, Änderungsanomalien.
4. Ja, redundante Daten können vorhanden sein, für bessere Verfügbarkeit oder Leistung.
5. Datenstrukturierung: Organisation und Formatierung. Kategorien: Felder, Datensätze, Tabellen, Datenbanken.
6. Tabellarische Darstellung von Mitarbeiterdaten mit verschiedenen Attributen.


Löschen in professionellen Datenbanken
Der SQL DELETE-Befehl führt zu Informationsverlust.
Das Löschen von Datensätzen führt zum Verlust von Beziehungen und Historie.
Alternative: Datensätze als inaktiv markieren oder Austrittsdaten hinzufügen.
Beispiel: Anstatt Mitarbeiterdaten zu löschen, ein Austrittsdatum eintragen.
Datenintegrität
Eindeutigkeit/Datenkonsistenz: Vermeidung von Duplikaten.
Referenzielle Integrität: Konsistenz zwischen verknüpften Tabellen.
Datentypen: Verwendung korrekter Datentypen für Felder.
Datenbeschränkungen: Sicherstellung der Validität der Daten.
Validierung: Prüfung der Daten vor dem Einfügen.
FK-Constraint-Optionen
ON DELETE NO ACTION: Löschen nur möglich, wenn kein Fremdschlüssel existiert.
ON DELETE CASCADE: Löschen führt zum Löschen verknüpfter Datensätze.
ON DELETE SET NULL: Fremdschlüssel werden auf NULL gesetzt.
ON DELETE DEFAULT: Fremdschlüssel werden auf einen Default-Wert gesetzt.
Aufgaben
Löschen in Datenbanken:

Aufgaben
