# Datenschutz und DSGVO

## Grundsätze

- **Keine Drittserver, keine Telemetrie.** Peerfold spricht nur mit Geräten im eigenen Netz und mit dem Postfach, das die Nutzer selbst eintragen. Es gibt keine Update-Prüfung, keine Fehlerberichte und keine öffentlichen STUN-, Signaling- oder Tracker-Dienste. Direktverbindungen (ab 1.1) werden über das eigene Postfach vermittelt; STUN/TURN-Server kommen nur zum Einsatz, wenn die Nutzer eigene eintragen.
- **Datenminimierung.** Im Postfach liegen nur verschlüsselte Objekte mit gehashten Namen. Gerätenamen, Dateinamen und Inhalte sind für den Anbieter nicht lesbar.
- **Speicherbegrenzung.** Postfach-Objekte werden gelöscht, sobald alle Mitglieder sie haben, spätestens nach der eingestellten Aufbewahrungsfrist (Standard 30 Tage).

## Welche Daten wo anfallen

| Ort | Daten | Lesbar für |
|---|---|---|
| Geräte der Mitglieder | Dateien des geteilten Ordners, Index, Gerätenamen und Geräte-IDs aller Mitglieder | Mitglieder |
| Lokales Netz | Verschlüsselter Datenverkehr; UDP-Beacons mit Geräte-ID, Port und gehashten Ordner-IDs | Inhalte: Mitglieder; Beacons: alle im Netz |
| Direktverbindung (WebRTC) | Verschlüsselter Datenverkehr; die Gegenseite sieht beim Verbindungsaufbau die IP-Adressen des Geräts | Mitglieder |
| Eigener STUN/TURN-Server (optional) | IP-Adressen, Zeitpunkte; bei TURN zusätzlich das verschlüsselte Datenvolumen | Betreiber des Servers |
| Postfach (WebDAV/S3) | Verschlüsselte Objekte, Größen, Zeitpunkte; verschlüsselte Signalisierung für Direktverbindungen | Inhalte: Mitglieder |
| Postfach-Anbieter (Protokolle) | IP-Adressen, Zeitpunkte, Zugangskennung | Anbieter |

## Löschkonzept

| Ereignis | Was passiert |
|---|---|
| Datei im geteilten Ordner gelöscht | Bei allen Mitgliedern in den System-Papierkorb. Leeren erfolgt durch die Nutzer selbst. |
| Mitglied verlässt den Ordner | Es löscht seine Schlüssel, seinen Index im Postfach und seinen lokalen Zustand. Die Dateien in seinem Vault bleiben, denn sie gehören ihm. |
| Besitzer entfernt ein Mitglied | Neuer Ordnerschlüssel; Index und Schlüsselumschlag des Mitglieds werden aus dem Postfach gelöscht. |
| Besitzer beendet die Freigabe | Mitgliederliste wird als beendet markiert, Indizes und Blöcke im Postfach werden gelöscht. |
| Aufbewahrungsfrist abgelaufen | Blöcke werden aus dem Postfach gelöscht, auch wenn sie noch nicht alle abgeholt haben. |

## Hinweise für die geschäftliche Nutzung

- Wer ein Postfach bei einem Anbieter nutzt, verarbeitet dort personenbezogene Daten im Auftrag (Art. 28 DSGVO). Mit dem Anbieter ist ein **Vertrag zur Auftragsverarbeitung** zu schließen. Die Inhalte sind zwar Ende-zu-Ende-verschlüsselt, Metadaten wie IP-Adressen fallen aber an.
- Empfohlen: Anbieter mit Sitz und Rechenzentrum in der EU, oder eine eigene Nextcloud.
- Für das Postfach ein eigenes App-Passwort beziehungsweise eigene Zugangsschlüssel anlegen. Diese landen in Einladungen, wenn der Postfach-Zugang mitgeschickt wird.

## Vorlage: Datenschutzhinweis für ein Team

> **Gemeinsame Notizen mit Peerfold**
>
> Wir teilen den Ordner „[Name]“ mit dem Obsidian-Plugin Peerfold. Beteiligt sind die Geräte der Mitglieder: [Namen].
>
> **Welche Daten:** Inhalte des Ordners, Gerätenamen und Geräte-IDs der Mitglieder.
>
> **Wo:** auf den Geräten der Mitglieder und verschlüsselt im Postfach bei [Anbieter, Ort]. Verbinden sich Geräte direkt, sehen sie gegenseitig ihre IP-Adressen. Der Anbieter kann die Inhalte nicht lesen; er sieht IP-Adressen, Zeitpunkte und Datenmengen. Mit ihm besteht ein Vertrag zur Auftragsverarbeitung.
>
> **Wie lange:** im Postfach, bis alle Mitglieder die Daten abgeholt haben, höchstens [30] Tage. Auf den Geräten, bis die Mitglieder sie löschen.
>
> **Verantwortlich:** [Name, Kontakt]. Auskunft, Berichtigung und Löschung: [Kontakt].
