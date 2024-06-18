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
SELECT COUNT(*) AS anzahl_schueler_mit_samsung_or_htc
FROM schueler s
JOIN smartphones v ON s.id = v.schueler_id
WHERE v.marke IN ('Samsung',

j.

SELECT COUNT(*) AS anzahl_schueler_in_emmendingen
FROM schueler s
JOIN lehrer_zugeordnet_schueler lzs ON s.id = lzs.schueler_id
JOIN lehrer l ON lzs.lehrer_id = l.id
JOIN ort o ON s.wohnort_id = o.id
WHERE l.name = 'Bohnert' AND o.name = 'Emmendingen';


k.

SELECT COUNT(*) AS anzahl_schueler_unterrichtet_von_zelawat
FROM schueler s
JOIN lehrer_zugeordnet_schueler lzs ON s.id = lzs.schueler_id
JOIN lehrer l ON lzs.lehrer_id = l.id
WHERE l.name = 'Zelawat';


l.

SELECT COUNT(*) AS anzahl_russische_schueler_unterrichtet_von_zelawat
FROM schueler s
JOIN lehrer_zugeordnet_schueler lzs ON s.id = lzs.schueler_id
JOIN lehrer l ON lzs.lehrer_id = l.id
WHERE l.name = 'Zelawat' AND s.nationalitaet = 'RUS';


m.

SELECT l.id, l.name, l.gehalt
FROM lehrer l
WHERE l.gehalt = (SELECT MAX(gehalt) FROM lehrer);

Tag 6

Teil 1 (Skalare Subquery)
1 Welches ist das teuerste Buch in der Datenbank?
  SELECT titel, verkaufspreis
FROM buecher
ORDER BY verkaufspreis DESC
LIMIT 1;

1 Welches ist das billigste Buch in der Datenbank?
  SELECT titel, verkaufspreis
FROM buecher
ORDER BY verkaufspreis ASC
LIMIT 1;

1 Lassen Sie sich alle Bücher ausgeben, deren Einkaufspreis über dem durchschnittlichen Einkaufspreis aller Bücher in der Datenbank liegt.

SELECT titel, einkaufspreis
FROM buecher
WHERE einkaufspreis > (SELECT AVG(einkaufspreis) FROM buecher);


  1 Lassen Sie sich alle Bücher ausgeben, deren Einkaufspreis über dem durchschnittlichen Einkaufspreis der Thriller liegt.
sql.

SELECT b.titel, b.einkaufspreis
FROM buecher b
JOIN buecher_has_sparten bhs ON b.buecher_id = bhs.buecher_buecher_id
JOIN sparten s ON bhs.sparten_sparten_id = s.sparten_id
WHERE s.bezeichnung = 'Thriller'
  AND b.einkaufspreis > (SELECT AVG(b2.einkaufspreis)
                         FROM buecher b2
                         JOIN buecher_has_sparten bhs2 ON b2.buecher_id = bhs2.buecher_buecher_id
                         JOIN sparten s2 ON bhs2.sparten_sparten_id = s2.sparten_id
                         WHERE s2.bezeichnung = 'Thriller');


  1 Lassen Sie sich alle Thriller ausgeben, deren Einkaufspreis über dem durchschnittlichen Einkaufspreis der Thriller liegt.

  SELECT b.titel, b.einkaufspreis
FROM buecher b
JOIN buecher_has_sparten bhs ON b.buecher_id = bhs.buecher_buecher_id
JOIN sparten s ON bhs.sparten_sparten_id = s.sparten_id
WHERE s.bezeichnung = 'Thriller'
  AND b.einkaufspreis > (SELECT AVG(b2.einkaufspreis)
                         FROM buecher b2
                         JOIN buecher_has_sparten bhs2 ON b2.buecher_id = bhs2.buecher_buecher_id
                         JOIN sparten s2 ON bhs2.sparten_sparten_id = s2.sparten_id
                         WHERE s2.bezeichnung = 'Thriller');


  1 Lassen Sie sich alle Bücher ausgeben, bei denen der Gewinn überdurchschnittlich ist; bei der Berechnung des Gewinndurchschnitts berücksichtigen Sie NICHT das Buch mit der id 22.

  SELECT titel, (verkaufspreis - einkaufspreis) AS gewinn
FROM buecher
WHERE (verkaufspreis - einkaufspreis) > (SELECT AVG(verkaufspreis - einkaufspreis)
                                         FROM buecher
                                         WHERE buecher_id != 22);

Teil 2 (Subquery nach FROM)

1. Summe der durchschnittlichen Einkaufspreise der Sparten (ohne Humor und Sparten mit durchschnittlichem Einkaufspreis ≤ 10 Euro)

SELECT SUM(avg_einkaufspreis) AS sum_avg_einkaufspreis
FROM (
    SELECT s.bezeichnung, AVG(b.einkaufspreis) AS avg_einkaufspreis
    FROM buecher b
    JOIN buecher_has_sparten bhs ON b.buecher_id = bhs.buecher_buecher_id
    JOIN sparten s ON bhs.sparten_sparten_id = s.sparten_id
    WHERE s.bezeichnung != 'Humor'
    GROUP BY s.bezeichnung
    HAVING avg_einkaufspreis > 10
) AS subquery;

2. Anzahl der bekannten Autoren (mehr als 4 Bücher veröffentlicht)

   SELECT COUNT(*) AS anzahl_bekannte_autoren
FROM (
    SELECT a.vorname, a.nachname, COUNT(ab.buecher_buecher_id) AS anzahl_buecher
    FROM autoren a
    JOIN autoren_has_buecher ab ON a.autoren_id = ab.autoren_autoren_id
    GROUP BY a.autoren_id
    HAVING anzahl_buecher > 4
) AS subquery;

3.  Verlage mit durchschnittlichem Gewinn pro Buch < 10 Euro (und Überprüfung, ob diese im Schnitt höchstens 7 Euro pro Buch verdienen)

   SELECT AVG(gewinn) AS avg_gewinn
FROM (
    SELECT v.name, AVG(b.verkaufspreis - b.einkaufspreis) AS gewinn
    FROM verlage v
    JOIN buecher b ON v.verlage_id = b.verlage_verlage_id
    GROUP BY v.verlage_id
    HAVING gewinn < 10
) AS subquery
WHERE gewinn <= 7;


Auftrag mit Tutorial

1. Tutorisl
2. Welcher Zeichensatz ist standardmässig bei ihrem DBMS eingestellt?
   MySQL
3. Versuchen Sie, das CSV File Personen in eine Tabelle einzulesen. Untersuchen Sie die CSV-Datei zuerst: Trennzeichen(Delimiter), ", Spaltennamen, Zeichensatz, Datumformat, ...
   Untersuchen

  
   






