Autotool-Tutorium
=================

Tutorium zum HaL-10 (am 5.12.2015 von 9:30 Uhr bis 11:00 Uhr)

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
