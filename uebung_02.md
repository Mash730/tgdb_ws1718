# Tutorium - Grundlagen Datenbanken - Blatt 2

## Vorbereitungen
* Für dieses Aufgabenblatt wird die SQL-Dump-Datei `tutorium.sql` benötigt, die sich im Verzeichnis `sql` befindet.
* Die SQL-Dump-Datei wird in SQL-Plus mittels `start <Dateipfad/zur/sql-dump-datei.sql>` in die Datenbank importiert.
* Beispiele
  * Linux `start ~/Tutorium.sql`
  * Windows `start C:\Users\max.mustermann\Desktop\Tutorium.sql`

## Datenbankmodell
![Datenbankmodell](./img/datamodler_schema.png)

## Aufgaben

### Aufgabe 1
Schaue dir das Datenbankmodell an. Wofür steht hinter dem Datentyp `NUMBER` die Zahlen in den runden Klammern?
Nehme dir die Oracle [Dokumentation](https://docs.oracle.com/cd/B28359_01/server.111/b28318/datatype.htm#CNCPT012) zu Hilfe.

#### Lösung
Der Datentyp `NUMBER` ermöglicht das speichern von positiven als auch negativen Ganzzahlen und Fließkommazahlen. Die Werte in den Klammern haben unterschiedliche Bedeutungen. Die erste Stelle in der Klammer steht für die Gesamte Anzahl von Zahlen und die zweite Stelle, wie viele Zahlen hinter dem Komma stehen.

Einige Beispiele:

| Deklaration   | Beispielmöglichkeiten                   |
| ------------- | --------------------------------------- |
| NUMBER(38,0)  | 9999999999999999999999999999999999999   |
| NUMBER(3,2)   | 1.81, 9.74, 0.54                        |
| NUMBER(5,2)   | 842.52, 965.45, 14.45                   |

### Aufgabe 2
Was bedeuten die durchgezogenen Linien, die zwischen einigen Tabellen abgebildet sind?

#### Lösung


### Aufgabe 3
Was bedeutet die gestrichelte Linie, die zwischen der Tabelle `ACC_VEHIC` und `GAS_STATION` abgebildet ist?

#### Lösung
-- nicht identifizierbare Beziehung. DEFAULT_GAS_STATION ist nur ein FK, der nicht zum PK gehört.

### Aufgabe 4
Die folgende Abbildung beschreibt eine Beziehung zwischen Tabellen. Sie wird auch `n` zu `m` Beziehung genannt. Beschreibe kurz die Bedeutung dieser Beziehung.
Nehme dir diesen [Artikel](https://glossar.hs-augsburg.de/Beziehungstypen) zu Hilfe.

![n-to-m-relationship](./img/n-to-m-relationship.png)

-- Es liegt eine 1 zu n verbindung vor

### Aufgabe 5
Was bedeutet der Buchstabe `P` und `F` neben den Attributen von Tabellen?

#### Lösung

-- Primary Key oder Foreign Key

### Aufgabe 6
Importiere die SQL-Dump-Datei in dein eigenes Schema. Wie lautet dazu der Befehl um dem import zu starten?

#### Lösung
```sql

START tutorium.sql

```

### Aufgabe 7
Gebe alle Datensätze der Tabelle `ACCOUNT` aus.

#### Lösung
```sql

SELECT *
FROM ACCOUNT;

```

### Aufgabe 8
Modifiziere Aufgabe 6 so, dass nur die Spalte `ACCOUNT_ID` ausgegeben wird.

#### Lösung
```sql
SELECT ACCOUNT_ID
FROM ACCOUNT;
```

### Aufgabe 9
Gebe alle Spalten der Tabelle `VEHICLE` aus.

#### Lösung
```sql
SELECT *
FROM VEHICLE;
```

### Aufgabe 10
Kombiniere Aufgabe 7 und 8 so, dass nur Personen (`ACCOUNT`) angezeigt werden, die ein Auto (`VEHICLE`) besitzen.

#### Lösung
```sql
SELECT SURNAME
FROM ACCOUNT
INNER JOIN ACC_VEHIC
ON ACCOUNT.ACCOUNT_ID = ACC_VEHIC.ACCOUNT_ID;


```

### Aufgabe 11
Modifizierde die Aufgabe 9 so, dass nur die Person mit der `ACCOUNT_ID` = `7` angezeigt wird.

#### Lösung
```sql
SELECT SURNAME
FROM ACCOUNT
INNER JOIN ACC_VEHIC
ON ACCOUNT.ACCOUNT_ID = ACC_VEHIC.ACCOUNT_ID
WHERE ACCOUNT_ID = 7;
```

### Aufgabe 12
Erstelle für dich einen neuen Benutzer.
> Achtung, nutze für die Spalten `C_DATE` und `U_DATE` vorerst die Syntax `SYSDATE` - [Dokumentation](https://docs.oracle.com/cd/B19306_01/server.102/b14200/functions172.htm)

#### Lösung
```sql
Insert into ACCOUNT (ACCOUNT_ID,SURNAME,FORENAME,EMAIL,C_DATE,U_DATE)
values('10','Wolf','Nico','wolfni@fh-trier.de',SYSDATE, to_date('15.09.17','DD.MM.RR'));

```

### Aufgabe 13
Erstelle für deinen neuen Benutzer ein neues Auto. Dieses Auto dient als Vorlage für die nächten Aufgaben.

#### Lösung
```sql


Insert into VEHICLE (VEHICLE_ID,VEHICLE_TYPE_ID,PRODUCER_ID,VERSION,DEFAULT_GAS_ID,PS,BUILD_YEAR,DOORS,C_DATE,U_DATE) values ('1','1','1','Ford','1','75',to_date('18.08.08','DD.MM.RR'),'5',to_date('15.09.17','DD.MM.RR'),to_date('15.09.17','DD.MM.RR'));

```

### Aufgabe 14
Verknüpfe das aus Aufgabe 12 erstellte neue Auto mit deinem neuen Benutzer aus Aufgabe 11 in der Tabelle `ACC_VEHIC` und erstelle den ersten Rechnungsbeleg.

#### Lösung
```sql
Deine Lösung
```

### Aufgabe 15
Ändere den Vorname `SURNAME` des Datensatzes mit der ID `7` in der Tabelle `ACCOUNT` auf `Zimmermann`.

#### Lösung
```sql
Deine Lösung
```

### Aufgabe 16
Speichere alle Änderungen deiner offenen Transaktion. Wie lautet der SQL-Befehl dazu?

#### Lösung
```sql
Deine Lösung
```
