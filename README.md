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
FROM kunden AS kundenliste
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

2. Aufgabe
   ![image](https://github.com/Jayjay2006Y/M164/assets/169802570/99750fba-cc71-4d55-9818-f3fd3b4264dc)










Setzen Sie diese Aufgaben um:
a.	Welches ist das niedrigste/höchste Gehalt eines Lehrers?
b.	Was ist das niedrigste Gehalt, das einer unserer Mathelehrer bekommt?
c.	Was ist der beste Notendurchschnitt der Noten Deutsch/Mathe?
d.	Wie viel Einwohner hat der größte Ort, wie viel der Kleinste? Ausgabe "Höchste Einwohnerzahl", "Niedrigste Einwohnerzahl"
e.	Wie groß ist die Differenz zwischen dem Ort mit den meisten und dem mit den wenigsten Einwohnern (z.B.: kleinster Ort hat 1000 Einwohner, größter Ort hat 3000 - Differenz ist 2000). Ausgabe einer Spalte "Differenz".
f.	Wie viele Schüler haben wir in der Datenbank?
g.	Wie viele Schüler haben ein Smartphone?
h.	Wie viele Schüler haben ein Smartphone der Firma Samsung oder der Firma HTC?
i.	Wie viele Schüler wohnen in Waldkirch?
j.	Wie viele Schüler, die bei Herrn Bohnert Unterricht haben, wohnen in Emmendingen?
k.	Wie viele Schüler unterrichtet Frau Zelawat?
l.	Wie viele Schüler russischer Nationalität unterrichtet Frau Zelawat?
m.	Welcher Lehrer verdient am meisten? (Achtung: Falle! Überprüfen Sie Ihr Ergebnis.)


Lösungen

a. SELECT MIN(gehalt) AS niedrigstes_gehalt, MAX(gehalt) AS hoechstes_gehalt
FROM lehrer;

b. SELECT MIN(gehalt) AS niedrigstes_gehalt
FROM lehrer l
JOIN lehrer_zugeordnet_faecher lzf ON l.id = lzf.idLehrer
JOIN faecher f ON lzf.idFach = f.id
WHERE f.fachbezeichnung = 'Mathe';

c. SELECT MIN((noteMathe + noteDeutsch) / 2.0) AS bester_notendurchschnitt
FROM schueler;

d. SELECT MAX(einwohnerzahl) AS hoechste_einwohnerzahl, MIN(einwohnerzahl) AS niedrigste_einwohnerzahl
FROM ort;

e. SELECT (MAX(einwohnerzahl) - MIN(einwohnerzahl)) AS differenz
FROM ort;

f. SELECT COUNT(*) AS anzahl_schueler
FROM schueler;

g. SELECT COUNT(*) AS anzahl_schueler_mit_smartphone
FROM schueler
WHERE besitztSmartphone = 1;

h.  SELECT COUNT(*) AS anzahl_schueler_mit_samsung_or_htc
FROM schueler s
JOIN smartphones v ON s.id = v.schueler_id
WHERE v.marke IN ('Samsung',

i. 
### i. Wie viele Schüler wohnen in Waldkirch?

```sql
SELECT COUNT(*) AS anzahl_schueler_in_waldkirch
FROM schueler s
JOIN ort o ON s.wohnort_id = o.id
WHERE o.name = 'Waldkirch';
















