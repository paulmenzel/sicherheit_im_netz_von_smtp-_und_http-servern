% Sicherheit im Netz von SMTP- und HTTP-Servern
% Paul Menzel (Max-Planck-Institut für molekulare Genetik)
% 9. November 2017

## Wer bin ich?

![Logo of Max Planck Institute for Molecular Genetics](images/MPIMG_helix_rgb.png){ height=25% }\


- Systemarchitekt beim [Max-Planck-Institut für molekulare Genetik](https://www.molgen.mpg.de/)
- Diplom-Wirtschaftsmathematiker an [TU Berlin](https://www.tu-berlin.de/)
- FLOSS-Befürworter

# Problemstellung

## Ziel

-  Sichere Übertragung von Daten
-  Geheim und authentifiziert

## Angriffsmodell

-  Annahme: Keine Übernahme der Server durch Angreifer
-  Mittelsmannangriff

### Realistisch?

-  DFN-Netz separat vom „Internet“
-  Netzwerkgeräte meist im Ausland produziert und enthält BLOBs
-  Snowden-Veröffentlichungen zeigen, dass realistisch.

## Lösungen

-  TLS
   -  Zertifikatsstellen
   -  [Monkeysphere Project](http://web.monkeysphere.info/)
-  DANE

### Nur bei SMTP

-  Ende-zu-Ende-Verschlüsselung (PGP/GPG, S/MIME)

# Angriffe

## Poodle, DROWN, …

Verschiedene Angriffe.

1.  Downgrade-Attacke (STARTTLS)
2.  Poodle, DROWN
3.  Unsichere Chiffren

## Sichere Konfiguration

1.  [BetterCrypto.org](https://bettercrypto.org/)
1.  [Mozilla Wiki: Security/Server Side TLS](https://wiki.mozilla.org/Security/Server_Side_TLS)
1.  [Cipherli.st](https://cipherli.st/)

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

# Ausblick

## Sicherheit der Serverprogramme

-   Problem: Dienste von überall erreichbar
-   Beliebige Eingabe (Analyseprogramme (Spam, Virenschutz), Formulare)
-   Untersuchung der Sicherheit der Server
    -   SMTP: Postfix, Exim, …
    -   HTTP: Apache HTTP Server, Nginx, …

# Fragen
