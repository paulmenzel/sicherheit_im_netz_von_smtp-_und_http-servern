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

# Verbreitung bei MPG

## Werkzeuge

- [Nmap](https://nmap.org/)
- [SSLyze](https://nabla-c0d3.github.io/)

# Fragen
