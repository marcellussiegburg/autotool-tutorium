Autotool-Tutorium
=================

Tutorium zum HaL-10 (am 5.12.2015 von 9:15 Uhr bis 10:45 Uhr)

Bitte *vor* HaL-10 die [Vorbereitungen](Prepare.md) durchführen. Probleme dabei können direkt [hier](https://github.com/marcellussiegburg/autotool-tutorium/issues) gemeldet werden.


Arbeiten mit der Autotool-VM
----------------------------

### Kompilieren des Autotool Backends

```bash
vagrant ssh
cd tool/yesod
cabal install ../server-implementation ../collection
sudo install -g apache -o apache /home/vagrant/tool/yesod/.cabal-sandbox/bin/autotool.cgi /var/www/cgi-bin/
```

### Kompilieren des Autotool Frontends

```bash
vagrant ssh
cd tool/yesod
yesod devel
```

Aufgaben
--------

### Back-End:

vervollständige diesen Lückentext: <http://autolat.imn.htwk-leipzig.de/gitweb/?p=tool;a=blob;f=collection/src/Prime/Certificate.hs;h=c78d1628fd1e33ea78cbfe379b8414d29928c902;hb=for-ghc-7.8>

### Front-End:

 - Wandeln der Listendarstellung bei Vorlesungen zu tabellarischer Darstellung
 - Sortierbarkeit der Tabellarischen Darstellung bei Vorlesungen ermöglichen (durch hinzufügen einer Route)

Mögliche Lösung:
 - siehe https://github.com/marcellussiegburg/autotool/tree/hal-10 z.Bsp. durch `git pull` im Verzeichnis `/home/vagrant/tool` in der VM
 - Direktsprung zu den [Änderungen für Tabellendarstellung](https://github.com/marcellussiegburg/autotool/commit/2c791599eb2783ba91c94b71d5b0927ca7685160)
 - Direktsprung zu den [Änderungen für Sortierung von Tabellen per Route](https://github.com/marcellussiegburg/autotool/commit/fd2764c48bcadab81610345b71d2de3f3cc78d53)

Hintergrund
-----------

zur Benutzung von autotool: mehrere Beiträge in <http://www.imn.htwk-leipzig.de/~waldmann/talk/>

Issues: <http://nfa.imn.htwk-leipzig.de/bugzilla/buglist.cgi?component=autotool&list_id=88&product=Auto*&resolution=--->
