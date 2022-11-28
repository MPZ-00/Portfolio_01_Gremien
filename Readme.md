# ER-Diagramm für Gremien-Datenbank
> An einer Hochschule werden viele Entscheidungen von Gremien vorbereitet und getroffen, z. B. vom
> Fachbereichsrat oder vom Prüfungsausschuss. Für die Verwaltung der Gremien und deren Arbeit soll
> eine Datenbank erstellt werden. Entwerfen Sie für diese Aufgabe eine Datenbankstruktur. Zeichnen
> Sie dazu Entity-Sets, Attribute und Relationen, wie Sie der unten stehenden Beschreibung
> entsprechen, in ein Entity-Relationship-Diagramm. Achten sie darauf, ...
>-   dass Sie ein ER-Diagramm erstellen sollen und nicht ein Diagramm einer relationalen
    Tabellenstruktur, d.h. M:N-Relationen sind noch nicht in Verbindungstabellen umgewandelt, es
    gibt mehrwertige Attribute, und eine Strukturierung in Unter-Entities (Unterklassen) ist möglich.
>-   dass Sie die Art der Relationen in der ausführlichen **(min, max-Schreibweise** kennzeichnen.

## Beschreibung der Datenbank für Gremien
Unten stehende Informationen sollen in der Datenbank enthalten sein und effizient abgefragt werden
können. Informationen, die hier nicht genannt sind, brauchen auch nicht ins ER-Diagramm, selbst
wenn Sie sie für eine Speditions-Datenbank für sinnvoll erachten.

**Personen** sind Studenten, Professoren, Mitarbeiter, Lehrbeauftragte und sonstige Personen wie
Industrievertreter, Bürgermeister usw., die Funktionen an der Fachhochschule wahrnehmen. Beispiele:
Der Student Max Meier, männlich, ist am 15.7.2000 geboren, wohnt in Ravensburg in der Burgstr. 3,
studiert Angewandte Informatik seit dem 1.9.2018 und hat die Matrikelnr. 30456.

Zentrale Entity sind die **Gremien**. Es gibt *offizielle* Gremien, die eine gesetzliche Grundlage haben,
wie z. B. der Hochschulrat, der Senat, der Fakultätsrat des Fachbereichs Maschinenbau oder der
Prüfungsausschuss für Angewandte Informatik. Daneben gibt es auch inoffizielle Gremien, die für
besondere Aufgaben eingesetzt werden, z. B. SPO-Kommission für den Master in Informatik. Start
dieses Gremiums war der 1.10.2016. Es hat seine Arbeit am 30.4.2017 beendet.
Personen sind Mitglieder in Gremien. In dieser Relation wird nur der momentane Zustand
gespeichert. Eine historische Entwicklung wer wann Mitglied eines Gremiums war, ist nicht
vorgesehen. Funktion gibt an, welche Funktion ein Mitglied in einem Gremium ausübt, z. B.
Vorsitzende(r).

Die Arbeit der Gremien wird vorwiegend in **Sitzungen** durchgeführt. *Einladung_am* gibt das Datum
an, an dem die Einladung zur Sitzung verschickt wurde, *öffentlich* ist ein binäres Attribut, das angibt,
ob die Sitzung öffentlich ist oder nur für die Teilnehmer zugänglich. Sitzungen mehrerer Gremien
zusammen sind in der Datenbank nicht vorgesehen. Folgende Abfragen sollen möglich sein:
- Wann beginnt die Sitzung, wann endet sie? Wo findet die Sitzung statt?
- Zu welchem Gremium gehört die Sitzung?
- Welche Personen nehmen an der Sitzung teil? Ist jemand später gekommen oder früher
gegangen?
- Wer führt das Protokoll?

Suche nach allen **Tagesordnungspunkten** einer Sitzung. Jeder Tagesordnungspunkt hat einen *Titel*,
eine *Kurzbeschreibung* und (nach der Sitzung) einen *Protokolltext*. Eine Sitzung hat normalerweise
mehrere Tagesordnungspunkte.

In den Sitzungen können **Anträge** gestellt werden und darüber abgestimmt werden. Jeder Antrag hat
einen *Titel*, einen *Antragstext*, das *Ergebnis* der Abstimmung in Form von Ja-Stimmen, Nein-Stimmen
und Enthaltungen sowie einem Attribut angenommen. Jeder Antrag muss einem Tagesordnungspunkt
zugeordnet sein. Folgende Abfragen sollen möglich sein:
- Suche nach allen Anträgen zu einem Tagesordnungspunkt.
- Suche nach allen Anträgen, die eine bestimmte Person gestellt hat.
- Suche nach allen Personen, die einen bestimmten Antrag gestellt haben.

Bei den Sitzungen werden **Dokumente** verteilt, z. B. eine Excel-Tabelle über Deputatsstunden der
Professoren oder eine Grafik mit verschiedenen Vorschlägen für das Hochschul-Logo. Neben dem
eigentlichen Inhalt hat ein Dokument noch einen *Mime-Typ* (Art des Dokuments, z. B. Pixel-Bild,
pdf-Dokument oder Excel-Tabelle) und ein Erstellungsdatum. Folgende Abfragen sollen möglich sein:

- Suche nach allen Dokumenten zu einem Tagesordnungspunkt.
- Suche nach allen Tagesordnungspunkten, zu denen ein Dokument gehört.
- Suche nach allen Autoren eines bestimmten Dokuments.
- Suche nach allen Dokumenten, die eine bestimmte Person erstellt hat.

Jedes Gremium hat ein oder mehrere **Aufgabengebiete**, z. B. hat das Gremium "Öffentlichkeitsarbeit
im Fachbereich Elektrotechnik und Informatik" die Aufgabengebiete: "Kontakte zu Schulen pflegen",
"Werbebroschüren und Plakate gestalten", "Informationsveranstaltungen planen", "Internetseiten
gestalten und pflegen", "Presseartikel verfassen".