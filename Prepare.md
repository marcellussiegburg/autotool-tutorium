Vorbereitungen
==============

Bei Problemen bitte unter https://github.com/marcellussiegburg/autotool-tutorium/issues oder per E-Mail bei
[Marcellus Siegburg](mailto:marcellus.siegburg@stud.htwk-leipzig.de) melden.

Hintergrund
-----------

Um den Prozess der Benutzung des Autotools zu vereinfachen gibt es ein Projekt, das sich mit dessen
Bereitstellung in einer VM beschäftigt, das [Autobuildtool](https://github.com/marcellussiegburg/autobuildtool).

Die Virtuelle Maschine beinhaltet nach fertiger Bereitstellung unter anderem:
 - den Quelltext der Autotool-Abhängigkeit [Autolib](http://autolat.imn.htwk-leipzig.de/gitweb/?p=lib;a=summary)
 - den Quelltext des Autotool [Autotool](http://autolat.imn.htwk-leipzig.de/gitweb/?p=tool;a=summary) Backend und Frontends
 - Abhängige Software (MySQL, Git, Haskell, Cabal)
 - Die fertig kompilierten, ausführbaren Programme, die zum Autotool gehören (Autotool-Semantik-Server (Backend-Server),
   Autotool-Yesod (Neuer Frontend-Server), Programm zum Berechnen von High-Scores)

Installation
------------

Um die Dauer der Vorbereitung zu verkürzen, wird zum HaL-10 ein bereits vorkompiliertes Image bereitgestellt.

#### Benötigt werden:
 - `git` https://git-scm.com/downloads
 - `vagrant` https://www.vagrantup.com/downloads.html
 - `VirtualBox` https://www.virtualbox.org/wiki/Downloads

#### Danach sind folgende Schritte auszuführen:
```bash
git clone https://github.com/marcellussiegburg/autobuildtool.git autotool
cd autotool
vagrant box add centos65x64 http://autotool-test.imn.htwk-leipzig.de/hal2015/autotool-yesod-x.y.box
git submodule update --init
```

***Achtung***: Bei http://autotool-test.imn.htwk-leipzig.de/hal2015/autotool-yesod-x.y.box,
ist `x.y` durch eine unter http://autotool-test.imn.htwk-leipzig.de/hal2015/ verfügbare Version zu erseten.
`x.y` sollte man sich merken und kurz vor HaL-10 prüfen, ob eine neuere Version verfügbar ist
und die Schritte ggf. erneut auszuführen.

In der Datei im Verzeichnis `config/config.yaml` sind die Parameter folgendermaßen zu ändern:
```yaml
autotool::build_doc: false
autotool::sources::disable: true
```
Abschließend
```bash
vagrant up
```

Test
----

Nach Erstellung der VM folgende Befehle ausführen:
```bash
vagrant ssh
cd tool/yesod
yesod devel
```

***Achtung***: Das Terminal geöffnet lassen

In einem lokalen Browser kann nun http://localhost:3333 aufgerufen werden. Die Seite lädt sich selbst neu,
bis die Kompilation abgeschlossen ist, dann kann man sich mit den Benutzerdaten einloggen:

|Matrikelnummer:|0     |
|---------------|------|

|Passwort: |foobar|
|----------|------|

Wählt man [diese URL](http://localhost:3333/server/http:%2F%2Flocalhost%2Fcgi-bin%2Fautotool.cgi/aufgabe/Convert_To_NFA-Direct/konfiguration/%28%20Convert%0A%20%20%20%20%20%20%7B%20name%20=%20Nothing%0A%20%20%20%20%20%20,%20input%20=%20Exp%20%20%20%20a%20%28a%20+%20b%29%5E%2A%20b%20%0A%20%20%20%20%20%20%7D%0A,%20%5B%20Sane%20,%20Min_Size%20%20%20%204%0A%20%20,%20Max_Size%20%20%20%206%0A%20%20,%20Alphabet%20%20%20%20%28mkSet%20%20%20%20%22ab%22%29%20%5D%0A%29/id/40645#eingeben),
wird beim Einsenden einer Lösung, ein Automaten-Bild angezeigt.

Hinweis
-------

Nach dem Verwenden von `vagrant up` wird eine virtuelle Maschine erzeugt.

 * Mit `vagrant ssh` loggt man sich per ssh auf der virtuellen Maschine ein.
 * Mit `vagrant destroy` wird die virtuelle Maschine und alles, was auf ihr gespeichert ist vernichtet.
 * Mit `vagrant suspend` kann man die virtuelle Maschine in der Ruhezustand versetzen (sie braucht dann keine Systemressourcen mehr.
 * Mit `vagrant halt` kann man die virtuelle Maschine ausschalten.
 * Mit `vagrant up` startet man die virtuelle Maschine, weckt sie aus dem Ruhezustand oder erzeugt sie, falls sie nicht (mehr) existiert.

***Hinweis***: Wird die Maschine nicht in den Ruhezustand versetzt oder ausgeschalten (wenn sie nicht gebraucht wird), läuft sie weiter im Hintergrund und belegt Systemressourcen.
