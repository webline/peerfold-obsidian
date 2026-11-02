# Peerfold – Anleitung

Mit Peerfold teilst du einen Ordner deines Obsidian-Vaults mit anderen Menschen. Ihr arbeitet an denselben Notizen, Änderungen kommen nach dem Speichern bei allen an. Es gibt kein Konto und keinen Server des Herstellers; alles ist Ende-zu-Ende-verschlüsselt.

*English version: [guide.md](guide.md)*

## Inhalt

1. [Was du brauchst](#was-du-brauchst)
2. [Installation](#installation)
3. [Ersteinrichtung](#ersteinrichtung)
4. [Einen Ordner teilen](#einen-ordner-teilen)
5. [Einer Einladung folgen](#einer-einladung-folgen)
6. [Ein Postfach einrichten](#ein-postfach-einrichten)
7. [Direkt übers Internet](#direkt-übers-internet)
8. [Im Alltag](#im-alltag)
9. [Mitglieder verwalten](#mitglieder-verwalten)
10. [Probleme lösen](#probleme-lösen)
11. [Datenschutz](#datenschutz)

## Was du brauchst

- Obsidian ab Version 1.8.7 auf macOS, Windows oder Linux. Auf iPhone, iPad und Android läuft Peerfold nicht.
- Für die Zusammenarbeit über das eigene Netz hinaus: ein **Postfach**, also einen Online-Speicher, den alle Beteiligten erreichen. Das kann eine Nextcloud oder ein S3-Speicher sein ([Abschnitt 6](#ein-postfach-einrichten)).
- Einen Weg, um Einladungen vertraulich zu verschicken, z. B. einen Messenger mit Ende-zu-Ende-Verschlüsselung.

## Installation

### Über BRAT (empfohlen)

[BRAT](https://github.com/TfTHacker/obsidian42-brat) installiert Plugins, die noch nicht im offiziellen Verzeichnis stehen, direkt von GitHub und hält sie aktuell. Die Menüpunkte unten heißen so, wenn Obsidian auf Deutsch eingestellt ist; die englischen Namen stehen in Klammern.

1. Öffne in Obsidian die *Einstellungen* (Zahnrad unten links) und wähle links **Community-Plugins** (*Community plugins*). Steht dort **Community-Plugins aktivieren** (*Turn on community plugins*), klicke darauf.
2. Klicke neben „Community-Plugins“ auf **Durchsuchen** (*Browse*), suche nach **BRAT** (Autor: TfTHacker), klicke auf **Installieren** (*Install*) und danach auf **Aktivieren** (*Enable*). Schließe das Suchfenster.
3. Links in den Einstellungen steht jetzt unter „Community-Plugins“ der Eintrag **BRAT**. Öffne ihn und klicke im Abschnitt „Beta-Plugin-Liste“ auf **Beta-Plugin hinzufügen** (*Add beta plugin*).
4. Trage im Feld **Repository** `webline/peerfold-obsidian` ein. Lass bei der Version „neueste Version“ stehen, setze den Haken bei **Plugin nach der Installation aktivieren** (*Enable after installing the plugin*) und klicke auf **Plugin hinzufügen** (*Add plugin*).
5. Nach ein paar Sekunden ist Peerfold installiert und eingeschaltet; der Einrichtungsassistent öffnet sich. Falls nicht: *Einstellungen → Community-Plugins* und den Schalter bei **Peerfold** einschalten.

### Von Hand

1. Lade aus dem neuesten [Release](https://github.com/webline/peerfold-obsidian/releases/latest) die Dateien `main.js`, `manifest.json` und `styles.css` herunter.
2. Öffne deinen Vault-Ordner im Finder bzw. Explorer. Der Ordner `.obsidian` ist versteckt: Auf dem Mac blendest du ihn mit <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>.</kbd> ein.
3. Lege darin den Ordner `.obsidian/plugins/peerfold/` an und kopiere die drei Dateien hinein. Der Ordner muss genau `peerfold` heißen.
4. Öffne in Obsidian *Einstellungen → Community-Plugins*. Schalte den eingeschränkten Modus aus, lade die Liste neu und aktiviere **Peerfold**.

## Ersteinrichtung

Beim ersten Start öffnet sich der **Einrichtungsassistent**. Er führt in vier Schritten durch:

1. **Gerätename:** So sehen dich die anderen. Am klarsten ist ein Vorname mit Gerät, z. B. „Anna Laptop“.
2. **Verbindungswege:** lokales Netz und direkte Verbindung übers Internet. Beides ist standardmäßig an.
3. **Postfach:** was es ist und welche Möglichkeiten es gibt.
4. **Los geht's:** Ordner teilen oder einer Einladung folgen.

Du kannst den Assistenten jederzeit wieder öffnen: Befehlspalette (<kbd>Cmd</kbd>/<kbd>Strg</kbd>+<kbd>P</kbd>) → „Peerfold: Einrichtungsassistent öffnen“, oder *Einstellungen → Peerfold → Hilfe*.

> [!NOTE]
> Beim ersten Start fragt die Firewall deines Systems eventuell, ob Obsidian eingehende Verbindungen annehmen darf. Erlaube das für private Netze, sonst finden sich Geräte im selben Netz nicht.

## Einen Ordner teilen

1. Klicke im Dateibaum mit der rechten Maustaste auf den Ordner und wähle **Mit Peerfold teilen**.
2. Trage ein Postfach ein, wenn ihr nicht nur im selben Netz arbeitet, und klicke auf **Verbindung testen**. Ohne Postfach wählst du **Ohne Postfach**.
3. Peerfold prüft die Links im Ordner: Bilder und andere Anhänge, die außerhalb liegen, werden in den Unterordner `Anhänge` kopiert und die Links angepasst. Links auf Notizen außerhalb des Ordners werden gemeldet.
4. Es öffnet sich der Einladungsdialog. Lege fest, ob der Postfach-Zugang mitgeschickt wird, und klicke auf **Einladung kopieren**.
5. Füge den Text in eine E-Mail oder Nachricht ein und schick ihn ab. Er enthält eine kurze Anleitung und den Link zur Einladung.

Eine Einladung gilt für **ein Gerät** und **sieben Tage**. Für jede weitere Person oder jedes weitere Gerät erstellst du eine neue (Rechtsklick auf den Ordner → **Peerfold: Einladen …**).

> [!WARNING]
> Wenn du den Postfach-Zugang mitschickst, steht das Passwort in der Einladung. Schick sie deshalb am besten über einen Messenger mit Ende-zu-Ende-Verschlüsselung. Lege dafür ein eigenes App-Passwort an, das du jederzeit widerrufen kannst.

### Die Anfrage bestätigen

Sobald jemand die Einladung annimmt, erscheint bei dir ein Dialog mit Name und **Geräte-ID**. Die Person sieht ihre eigene Geräte-ID direkt nach dem Klick auf **Beitritt anfragen** (später auch unter *Einstellungen → Peerfold → Geräte-ID*). Lass sie dir am Telefon oder im Chat durchsagen und vergleiche ein paar Zeichengruppen, bevor du auf **Zustimmen** klickst. Danach bekommt das Gerät den Ordnerschlüssel und die Dateien.

Warum das Ganze: Wer die Einladung hat, kann damit eine Anfrage stellen. Der Vergleich stellt sicher, dass die Anfrage vom richtigen Gerät kommt und nicht von jemandem, an den die Einladung weitergeraten ist. Hast du die Einladung selbst über einen sicheren Weg verschickt und erwartest genau diese Anfrage, ist das Risiko gering.

## Einer Einladung folgen

1. Klicke auf den Link in der Einladung. Manche Mailprogramme machen nur den Anfang des langen Links klickbar, oder es öffnet sich nichts. Dann markiere die ganze Nachricht, kopiere sie und wähle in der Befehlspalette (<kbd>Cmd</kbd>/<kbd>Strg</kbd>+<kbd>P</kbd>) **Peerfold: Einladung annehmen …**. Peerfold übernimmt die Einladung aus der Zwischenablage, auch wenn der Link umbrochen ist.
2. Klicke bei **Ablage in deinem Vault** auf den Ordner-Knopf und wähle per Klick, wo der geteilte Ordner angelegt wird (z. B. `Geteilt`). Der Name ist schon vorgeschlagen; darunter siehst du, wo die Dateien landen.
3. Klicke auf **Beitritt anfragen**. Peerfold zeigt dir jetzt deine **Geräte-ID**. Die Person, die eingeladen hat, muss zustimmen und fragt dich vielleicht danach.
4. Nach der Zustimmung kommen die Dateien an. Im selben Netz dauert das Sekunden, über das Postfach bis zum nächsten Abgleich (Standard: eine Minute).

## Ein Postfach einrichten

Das Postfach braucht ihr, wenn ihr an verschiedenen Orten arbeitet oder nicht gleichzeitig online seid. Es dient auch zur Vermittlung der direkten Verbindung. Dort liegen nur verschlüsselte Daten mit unkenntlichen Namen.

### Nextcloud (WebDAV)

1. Melde dich in deiner Nextcloud an und lege einen Ordner an, z. B. `Peerfold`.
2. Lege ein **App-Passwort** an: Avatar oben rechts → *Persönliche Einstellungen → Sicherheit → Neues App-Passwort erstellen*. Name z. B. „Peerfold“.
3. Trage in Peerfold ein:

| Feld | Wert |
|---|---|
| Art | WebDAV |
| Adresse | `https://cloud.example.de/remote.php/dav/files/BENUTZERNAME/Peerfold/` |
| Benutzername | dein Nextcloud-Benutzername |
| Passwort | das App-Passwort |

Den genauen WebDAV-Pfad zeigt Nextcloud auch in der Dateiansicht unten links unter *Dateien-Einstellungen → WebDAV*.

Für mehrere Personen gibt es zwei Wege: Alle nutzen denselben Zugang (am einfachsten: Postfach-Zugang mit der Einladung verschicken), oder du gibst den Ordner in Nextcloud für die anderen frei und jede Person trägt ihren eigenen Zugang mit dem Pfad zum geteilten Ordner ein.

### S3-Speicher

Jeder S3-kompatible Speicher funktioniert, z. B. Hetzner Object Storage, IONOS oder ein eigener MinIO-Server. Beispiel Hetzner (Standort Falkenstein):

| Feld | Wert |
|---|---|
| Art | S3-kompatibel |
| Endpunkt | `https://fsn1.your-objectstorage.com` |
| Region | `fsn1` |
| Bucket | Name deines Buckets |
| Präfix | optional, z. B. `peerfold` |
| Access Key ID / Secret Access Key | aus der Konsole des Anbieters |
| Pfad-Stil | an |

Lege den Bucket vorher in der Konsole des Anbieters an und gib dem Schlüssel Lese- und Schreibrechte nur auf diesen Bucket.

### Postfach später ändern

*Einstellungen → Peerfold →* beim Ordner auf **Postfach** klicken. Alle Mitglieder müssen dasselbe Postfach nutzen. Wechselst du es, teile die neuen Zugangsdaten den anderen mit; sie tragen sie bei sich unter **Postfach** ein.

## Direkt übers Internet

Sind Geräte an verschiedenen Orten, versucht Peerfold eine direkte Verbindung (WebRTC). Den Aufbau vermittelt das Postfach; ein fremder Server ist nicht beteiligt.

- **Mit IPv6 auf beiden Seiten** klappt das ohne weiteres Zutun. Die meisten Glasfaser-, Kabel- und Mobilfunkanschlüsse haben IPv6. Ob deiner es hat, zeigt z. B. [test-ipv6.com](https://test-ipv6.com).
- **Mit reinem IPv4** hinter einem Router (NAT) klappt es meist nicht. Dann läuft der Abgleich über das Postfach weiter, nur etwas langsamer. Wer einen eigenen STUN- oder TURN-Server betreibt (z. B. coturn), trägt ihn unter *Einstellungen → Peerfold → Eigene STUN/TURN-Server* ein:

```text
stun:stun.example.de:3478
turn:benutzer:passwort@turn.example.de:3478
```

Welcher Weg gerade aktiv ist, zeigt das Statusfenster (Klick auf die Statusleiste) und die Mitgliederliste: „im LAN verbunden“ oder „direkt übers Internet verbunden“.

## Im Alltag

### Die Statusleiste

| Anzeige | Bedeutung |
|---|---|
| Icon und ✓ | alles abgeglichen |
| ↻ 3 | drei Dateien sind noch nicht bei allen angekommen |
| ✉ 1 | eine Beitrittsanfrage wartet auf dich |
| ⚠ | ein Problem; ein Klick zeigt Details |

### Hinweise bei Änderungen

Ändert oder löscht ein anderes Mitglied Dateien im geteilten Ordner, zeigt Peerfold einen Hinweis mit Namen, z. B. „Anna Laptop hat „Protokoll“ in „Projekt“ geändert.“ Bei einer einzelnen Notiz öffnet ein Klick auf den Namen die Notiz. Der Hinweis bleibt stehen, bis du ihn anklickst – so siehst du ihn auch, wenn du gerade nicht am Rechner warst. Weitere Änderungen fließen in denselben Hinweis ein. Hast du ihn weggeklickt, bleibt es für diesen Ordner 20 Minuten still. Abschalten kannst du das unter *Einstellungen → Peerfold → Benachrichtigungen*.

Dort steht unter *Hilfe* auch die installierte **Version**.

### Konflikte

Bearbeiten zwei Personen gleichzeitig dieselbe Notiz an verschiedenen Stellen, führt Peerfold die Änderungen zusammen. Überschneiden sie sich, bleibt eine Fassung in der Notiz und die andere landet als Kopie daneben:

```text
Plan (Konflikt Anna Laptop 2026-10-31 1955 UTC).md
```

Die Uhrzeit im Namen ist in UTC, damit der Name auf allen Geräten gleich ist. Übernimm, was du brauchst, und lösche die Kopie.

### Anhänge und Links

- Fügst du ein Bild ein, das außerhalb des geteilten Ordners liegt, kopiert Peerfold es beim Speichern in den Ordner `Anhänge`.
- Links auf Notizen außerhalb des Ordners sehen die anderen als unaufgelöst. Peerfold warnt dich; in den Einstellungen kannst du sie stattdessen in Klartext umwandeln lassen.
- Benennt jemand eine Datei um, werden die Links bei allen angepasst. Löscht jemand eine Datei, bleibt vom Link der Text stehen.
- Befehl **Verwaiste Anhänge im geteilten Ordner anzeigen** listet Anhänge, auf die keine Notiz mehr verweist. Entfernen verschiebt sie in den Papierkorb.

### Was du lassen solltest

- Den geteilten Ordner **zusätzlich** mit iCloud, Dropbox oder Obsidian Sync abgleichen. Nimm ihn dort aus, sonst arbeiten zwei Systeme gegeneinander.
- Einladungscodes in öffentliche Kanäle stellen.

## Mitglieder verwalten

- **Mitglieder ansehen:** Rechtsklick auf den Ordner → **Peerfold: Mitglieder**.
- **Jemanden entfernen** (nur wer geteilt hat): in der Mitgliederliste auf **Entfernen**. Das Gerät bekommt danach nichts Neues mehr und kann nicht wieder beitreten; was es schon hat, behält es.
- **Selbst aussteigen:** *Einstellungen → Peerfold →* beim Ordner **Verlassen**. Deine Dateien bleiben, Schlüssel und deine Daten im Postfach werden gelöscht.
- **Freigabe beenden** (nur wer geteilt hat): Alle bekommen keine Änderungen mehr, das Postfach wird geleert, die Dateien bleiben bei allen.
- **Neues Gerät** (z. B. ein zweiter Laptop): Jedes Gerät ist ein eigenes Mitglied und braucht eine eigene Einladung.

## Probleme lösen

| Was passiert | Mögliche Ursache | Was hilft |
|---|---|---|
| Die Beitrittsanfrage kommt nicht an | anderes Netz und kein Postfach in der Einladung | Einladung mit Postfach-Zugang neu erstellen |
| Geräte im selben WLAN finden sich nicht | Firewall blockiert Obsidian; Gäste-WLAN trennt Geräte | Obsidian in der Firewall erlauben; unter *Feste Adressen* die IP und den Port des anderen Geräts eintragen (z. B. `192.168.1.20:47322`) |
| „Zugang verweigert“ beim Postfach | falsches Passwort oder App-Passwort widerrufen | Zugang prüfen, **Verbindung testen** |
| „Nicht gefunden“ beim Postfach | Ordner oder Bucket fehlt, Adresse falsch | Ordner in Nextcloud bzw. Bucket anlegen, Adresse mit `/` am Ende |
| „n Datei(en) warten noch auf Daten“ | Das Gerät, das die Datei hat, ist offline und es gibt kein Postfach | warten, bis es online ist, oder Postfach einrichten |
| Keine direkte Verbindung | eine Seite ohne IPv6 | läuft übers Postfach weiter; optional eigener STUN/TURN-Server |
| „Zugriff entzogen“ | du wurdest aus dem Ordner entfernt | bei der Person nachfragen, die geteilt hat |

Hilft nichts davon: **Befehlspalette → Peerfold: Jetzt synchronisieren** stößt alles sofort an. Technische Meldungen stehen in der Entwicklerkonsole (<kbd>Cmd</kbd>+<kbd>Opt</kbd>+<kbd>I</kbd> bzw. <kbd>Strg</kbd>+<kbd>Shift</kbd>+<kbd>I</kbd>) mit dem Präfix `[Peerfold]`.

## Datenschutz

- Inhalte, Datei- und Gerätenamen sind für den Postfach-Anbieter nicht lesbar.
- Bei direkten Verbindungen sehen die Mitglieder gegenseitig ihre IP-Adressen.
- Peerfold sendet keine Telemetrie und kontaktiert keine anderen Server als dein Postfach und – falls eingetragen – deine STUN/TURN-Server.

Mehr dazu, inklusive einer Vorlage für einen Datenschutzhinweis im Team: [datenschutz.md](datenschutz.md).
