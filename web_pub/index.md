---
layout: default
title: Andrej Hoferica - Webové publikovanie
style: main
---
## Webové publikovanie
---

### Dokumentácia k 2. zadaniu z predmetu Webové publikovanie

&emsp;V dokumente DocBook týkajúcom sa zadania č. 2 som použil niekoľko základných elementov, ako napr. `<book>`, `<bookinfo>`, `<abstract>`, `<chapter>`, `<section>`, `<title>`, `<para>`, `<caption>`, `<emphasis>`, `<bibliography>` či `<appendix>`. Čo sa týka atribútov, tie som použil napríklad pri odkazoch na iné časti dokumentu, pri deklarovaní jazyka sekcie/knihy, číslovaní v dokumente, pri type zvýraznenia textu, pri načítavaní obrázka do dokumentu alebo pri deklarácii tabuľky. 

- Zvýraznenie slov kurzívou je použité na strane 10 a 11 pod obrázkami a na strane 19 cez klasický `<emphasis>`. Okrem toho som použil zvýraznenie slov tučným písmom na strane 15 prostredníctvom `<emphasis role="strong">`.
- Odkazy na iné časti dokumentu môžeme vidieť, samozrejme, v obsahu, ale aj priamo v texte, kde sa nachádzajú citácie. Tie sú tvorené elementom `<xref linkend="bib.1"/>`, kde `bib.1` je id položky v bibliografii. Dva odkazy na URL sú použité v bibliografii ako element `<ulink>`.
- Poznámky pod čiarou sa nachádzajú na strane 12 a 18 (spolu ich je 5). Vytvoril som ich elementom `<footnote>`.
- Obrázky nájdeme na stranách 10 a 11, tabuľku na strane 18. Ich zoznam je na strane 20 ako príloha. Obrázky s popisom sú vložené do jedného elementu `<mediaobject>`.
- Register pojmov je v samostatnej poslednej kapitole v závere dokumentu na strane 19. Obsahuje dvojúrovňový zoznam pojmov s linkami na sekcie, kde sa pojmy nachádzajú. Tu sú linky tvorené elementami `<link linkend="tag_sekcie">`.

---

### Dokumentácia k 1. zadaniu z predmetu Webové publikovanie

**Rozloženie (layouts):**

* `default.html` je takým rodičovským layoutom, kde includujem menu s linkami na prekliky na ostatné podstránky, footer s odkazmi na moje internetové profily, použitie štýlu a kde vkladám samotný content, tento layout je použitý napríklad na podstránke [O mne](/about), Webové publikovanie a aj na [hlavnej stránke](/)
* layout `cv.html` používam na podstránke so [životopisom](/cv), keďže svoj životopis som vyriešil formou neviditeľnej tabuľky
* layout `work.html` používam na podstránke o [mojej práci](/praca) na zadaniach, tvoria ho odrážky s obashom poľa na stránke `index.html` z priečinka 'praca'
* layout `gallery.html` je použitý na stránke s mojou [galériou](/galeria), najskôr obsahoval include so súborom na tvorbu galérie, ale neskôr som túto časť presunul do iného include súboru, keďže content stránky som chcel mať rozdelený na dve časti

__Premenné v sídle:__

- v template `gallery_template.html` - nadpis a suhlas, čo sú časti hlavnej stránky s galériou
- v súbore `image-gallery.html` - cisloPolozky, ktorú používam ako index na prístup k obsahu údajového súboru, file (iterácia súborov v sídle), z tejto premennej sú potom odvodené ďalšie - file.path (link na daný obrázok), file.extname, filenameparts (rozdelenie cesty súboru), filename (alternatívny text k obrázku), popis fotky a linku a aj link samotný je tiež vypísaný cez premennú z dátového súboru `popisy_fotiek.json`

&emsp;Premenné používam aj pri for cykloch alebo podmienkach, ako napr. pri iterácii údajového súboru a pri prístupe k jednotlivým častiam, alebo v `menu.html`, kde potrebujem zistiť, na ktorej stránke som, aby sa následne daný link podčiarkol.

__Zoznam premenných:__

nadpis, suhlas, cisloPolozky, file, site.static_files, file.path, include.folder, file.extname, filenameparts, filename, site.data.popisy_fotiek.metadata (a jej ďalšie zložky), page.title, content, site.data.udaje.hlavne_polozky (a jej ďalšie zložky), polozka (a jej ďalšie zložky), page.last_modified_at, page.zadania, odrazka, page.style

__Filtre:__

- v súbore `image-gallery.html`: split, last, replace, plus
- v layoute `default.html`: date

__Tagy:__

`for`, `if`, `include`, `assign`, `capture`

__Dátové súbory:__

- `popisy_fotiek.json` - využívam v galérií ako zdroj popisov a názvov
- `udaje.json` - v životopise sú všetky dáta brané z tohto súboru

__Pluginy:__

- `jekyll-sitemap` - vytvára mapu stránky v XML, funguje aj na Gite
- `jemoji` - v životopise pri hlavných názvoch mám aj primerane vhodné grafické emoji, taktiež funguje aj na Gite
- `jekyll-last-modofied-at` - na každej stránke je zobrazený dátum poslednej modifikácie stránky, funguje len na localhoste

__Štýl:__

- `main.css` - hlavný štýl, definované fonty, veľkosti a farby, taktiež definované stĺpce a riadky pre tabuľku v životopise

&emsp;Štýly som mal 3, trochu som s nimi experimentoval, no nakoniec som sa rozhodol všetko zjednotiť (typ fontu, veľkosť textu, farbu textu, šírku obrazovky, zarovnanie) pre lepšiu konzistenciu a krajší vzhľad.

&emsp;Na stránkach [Moja práca](/praca) a Webové publikovanie používam Markdown.

---

[![](./down.png)  Stiahnuť dokumentáciu k zadaniu č. 1 vo formáte PDF](./dokumentacia.pdf)

[![](./down.png)  Stiahnuť zadanie č. 1 ako ZIP archív](http://andrew141.github.io/web_pub/Z1-xhofericaa.zip)

[![](./down.png)  Stiahnuť zadanie č. 2 ako ZIP archív](http://andrew141.github.io/web_pub/Z2-xhofericaa.zip)