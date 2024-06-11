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

1. Select Alias

SELECT
FROM kunden AS kundentiste
WHERE kundentiste > 80000

SELECT kunde_id, name, postleitzahl
FROM kunden AS kundentiste
WHERE kundentiste.kunde_id > 80000;

2.

SELECT o.name,
FROM
ON
k. name,
AS
_ INNER JOIN
WHERE o.name LIKE

SELECT o.name, k.name
FROM kunden AS k
INNER JOIN ort AS o
ON k.fk_ort_postleitzahl = o.id_postleitzahl
WHERE o.name LIKE '%';  -- Placeholder for LIKE pattern

2. ![image](https://github.com/Jayjay2006Y/M164/assets/169802570/99750fba-cc71-4d55-9818-f3fd3b4264dc)




Aufgaben
