% Sicherheit im Netz von SMTP- und HTTP-Servern
% Paul Menzel (Max-Planck-Institut für molekulare Genetik)
% 9. November 2017

## Wer bin ich?

![Logo of Max Planck Institute for Molecular Genetics](images/MPIMG_helix_rgb.png){ height=25% }\


- Systemarchitekt beim [Max-Planck-Institut für molekulare Genetik](https://www.molgen.mpg.de/)
- Diplom-Wirtschaftsmathematiker ([TU Berlin](https://www.tu-berlin.de/))
- FLOSS-Befürworter

## Präsentation

Folien in Markdown mit Pandoc nach LaTeX-Beamer umgewandelt, verfügbar auf GitHub.

<https://github.com/paulmenzel/sicherheit_im_netz_von_smtp-_und_http-servern>

# Problemstellung

## Ziel

-  Sichere Übertragung von Daten
-  Geheim und authentifiziert

### Betrachtung in Vortrag

-  SMTP: Zwischen SMTP-Servern (MTA)

## Angriffsmodell

-  Annahme: Keine Übernahme der Server durch Angreifer
-  Annahme (SMTP): Vertrauen in Betreiber der Server auf Sender- und (Ziel-)Empfängerseite
-  Annahme (HTTP): Sicherer Browser, HTTP korrekt konfiguriert
-  Mittelsmannangriff

### Realistisch?

-  Innerhalb der MPG: DFN-Netz separat vom „Internet“ (Florida, CBS, …)
-  Netzwerkgeräte meist im Ausland produziert und enthalten BLOBs
-  Snowden-Veröffentlichungen zeigen, dass realistisch

## Lösungen (TLS)

-  SMTP: `STARTTLS`
-  HTTP: HTTPS (Port 443)

-  Zertifizierungsstellen (DFN, Let’s Encrypt)
-  [Monkeysphere Project](http://web.monkeysphere.info/)
-  DANE

### Nur bei SMTP

-  Ende-zu-Ende-Verschlüsselung (PGP/GPG, S/MIME)

## Zielumsetzung

### SMTP

-  Authentifizierung: Zustellung an korrekten Server
-  Schutz der Metadaten
-  geheime Übertragung auch bei nicht Ende-zu-Ende-Verschlüsselung

### HTTP

-  Authentifizierung: Kommunikation mit korrektem Server (Interaktion)
-  Datenschutz (Metadaten wie URL geschützt)
-  Verschlüsselung

# Angriffe

## Poodle, DROWN, …

Verschiedene Angriffe.

1.  Downgrade-Attacke (STARTTLS)
2.  Poodle, DROWN
3.  Unsichere Chiffren

## Sichere Konfiguration

<postmaster@….mpg.de> nach RFC 822 Pflicht!

1.  [BetterCrypto.org](https://bettercrypto.org/)
1.  [Mozilla Wiki: Security/Server Side TLS](https://wiki.mozilla.org/Security/Server_Side_TLS)
1.  [Cipherli.st](https://cipherli.st/)

## Ideal für SMTP

Mehrere Komponenten: DNS, Zertifikate

### TLS

-   MX-Eintrag stimmt mit Servernamen überein

### DANE

-  TLSA-DNS-Einträge

## Test

### WWW

1.  [Hardenize](https://www.hardenize.com/)
1.  [SSL-Tools](https://ssl-tools.net/)
1.  [SSL Server Test von Qualys SSL Labs](https://www.ssllabs.com/ssltest/analyze.html?d=login.rz.ruhr-uni-bochum.de)

### Kommandozeile

1.  OpenSSL, GnuTLS
1.  [Nmap](https://nmap.org/)
1.  [SSLyze](https://nabla-c0d3.github.io/)
1.  `posttls-finger`

## Beispiel zu posttls-finger

```
$ posttls-finger …
```

# MPG

## Zeitraum

-   8\. November 2017

# Inkorrekte MX-Einträge

## Beispiel GV

```
$ host mpg.de
[…]
$ host mx1.mpg.de
[…]
```

Keine Antwort von postmaster@mpg.de auf Nachricht.

## Problem Verwaltungsadressen

```
$ host vw.molgen.mpg.de
[…]
```

Bitte überprüfen!

# HTTP

## Problem

1.  Viele alte Dienste ohne HTTPS-Zertifikat, ohne ACME oder Wildcard-Zertifikate schwer zu handhaben
1.  Never-touch-a-running System

## Lösung

1.  SSL-Terminierung (HAProxy)
1.  Wechsel zu Let’s Encrypt und Skript, dass Zertifikate in Echtzeit erstellt

# Ausblick

## Sicherheit der Serverprogramme

-   Problem: Dienste von überall erreichbar
-   Beliebige Eingabe (Analyseprogramme (Spam, Virenschutz), Formulare)
-   Untersuchung der Sicherheit der Server
    -   SMTP: Postfix, Exim, …
    -   HTTP: Apache HTTP Server, Nginx, …

## Fazit

1.  MPG-Netz auch Vorbildwirkung
1.  Mehr Gewissenhaftigkeit
1.  Mehr Bewusstsein (DNSSEC, DFN)
1.  Ohne DANE keine automatische Konfiguration möglich, manuelle Konfiguration erforderlich

# Fragen
