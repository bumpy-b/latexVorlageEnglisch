## Vorlage verwenden
Pflichtangaben können direkt in `dokumentation.tex` geändert werden.
Kapitel werden in `content` nach dem Schema `<nn>kapitel.tex` angelegt, wobei &lt;nn&gt; eine mindestens zweistellige Zahl sein muss.
Das Logo der Firma kann durch das Ersetzen der Datei `images/logo.png` geändert werden. Die Größe des Bildes ändert man durch das Verkleinern/Vergrößern der Datei.

Hinweis: Unter Miktex 2.9 gibt es derzeit leider Probleme, die aber umgangen werden können. [Mehr dazu hier](https://github.com/dhbw-horb/latexVorlage/issues/23).

# Kompilierung
Für das Paket _latexmk_ und die Erzeugung eines Glossars muss ein Perl-Interpreter installiert sein. Linux- und Mac-User haben normalerweise diesen schon im System installiert. Windows-Nutzern ist ActivePerl zu empfehlen (http://www.activestate.com/activeperl/downloads). Die Vorlage nutzt außerdem _biblatex_ mit dem Backend _biber_ für die Bibliographie.

## Über latexmk:
* Bauen: `latexmk`
* Aufräumen: `latexmk -c`


## Benutzung mit makefile
	\make all			Generiert pdf in $output und loescht temporaere Files
	\make clean			loescht output
* Kompilieren:
  * `make` oder `make all` (Generiert pdf in $output und loescht temporäre Build-Dateien)
* Aufräumen:
  * `make clean` (entfernt output/, dokumentation.pdf und dokumentation.synctex.gz)
  * `make cleanup` (entfernt nur temporäre Build-Dateien)

## Ohne latexmk
Wenn kein latexmk installiert werden kann oder soll, stellt das makefile auch die entsprechenden Befehle ohne latexmk bereit: 
* `make all-legacy`
* `make clean-legacy`
* `make cleanup-legacy`

# Nur Deckblatt verwenden
```latex
\usepackage{pdfpages}
% .....
\includepdf[pages=1]{../latexVorlage/dokumentation.pdf}
```

# Ordnerstruktur
* **bibliographie.bib** - Einträge der Bibliographie
* **dokumentation.tex** - die Hauptdatei, die alles andere einbindet, hier werden z.B. die Pflichtangaben auf dem Deckblatt geändert
* **header.tex** - Präambel, wo die genutzten Packete und Layout-Einstellungen aufgeführt werden
* **latexmkrc** - die Regeln, nach denen latexmk das Dokument baut
* **content/** - enthält pro Kapitel eine Datei (Schema: `<nn>kapitel.tex`)
* **frontbackmatter/** - enthält Vor- und Nachspann-Dateien, die in dokumentation.tex eingebunden werden
	* **frontbackmatter/abstract.tex** - Abstract, kann sowohl in deutsch als auch in englisch oder beides eingetragen werden
	* **frontbackmatter/acronyms.tex** - Einträge des Abkürzungsverzeichnisses
	* **frontbackmatter/deckblatt.tex** - das Deckblatt, hier muss gewöhnlich nichts verändert werden, die Textelemente werden in dokumentation.tex eingetragen
	* **frontbackmatter/erklaerung.tex** - eidesstattliche Erklärung, normalerweise nichts zu verändern
	* **frontbackmatter/glossary.tex** - Einträge des Glossars
	* **frontbackmatter/literatur.tex** - Einträge der Bibliographie (veraltet, ohne BibLaTeX/Biber)
	* **frontbackmatter/sperrvermerk.tex** - Sperrvermerk (soweit benötigt --- falls nicht in dokumentation.tex auskommentieren), normalerweise nichts zu verändern
* **images/** - enthält Bilder und Logos
	* **images/logo.png** - Logo der Firma auf Deckblatt. zu ersetzen!

