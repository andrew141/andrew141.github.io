---
layout: default
title: Andrej Hoferica - Webové publikovanie
style: main
---
## Webové publikovanie
---

### Dokumentácia k 3. zadaniu z predmetu Webové publikovanie

&emsp;Na opis typu dokumentu som si vybral DTD. Elementov používam niekoľko, skúsim ich v stručnosti opísať:
- `<slideshow>` - hlavný koreňový element prezentácie zoskupujúci jednotlivé "slajdy"
- `<slide>` - ako už názov napovedá, je to element na zoskupenie častí v slajde, všetko v tomto elemente sa zobrazí na jednej stránke
- `<titulok>`, `<nadpis>` - elementy na zobrazenie nadpisu slajdu, každý slajd musí obsaovať jeden zo spomenutých elementov, rozdiel medzi nimi je ten, že `<nadpis>` je zobrazený len v hornej časti obrazovky, obsahuje iba text a elementu `<titulok>` môžeme zadávať parametre veľkosť písma a padding zhora, ktoré ale nie sú nevyhnutne potrebné
- `<telo>` - v tomto elemente budú všetky časti slajdu okrem titulku alebo nadpisu, môže obsahovať prakticky všetky ostatné elementy, ako napr. `<zarovnaj>`, `<zoznam>`, `<hruby_zoznam>`, `<obrazok>`, `<video>` alebo elementy `<lava_strana>` a `<prava_strana>`, od nadpisu alebo titulku je telo oddelené horizontálnou čiarou
- `<zarovnaj>` - element, v ktorom všetko bude zarovnané tak, ako bude napísané v atribúte, t.j. vľavo, vpravo, na stred alebo roztiahnuté na šírku obrazovky, v elemente môžeme mať odsek, video alebo obrázok
- `<zoznam>`, `<hruby_zoznam>` - elementy na zobrazenie nejakého nečíslovaného obsahu, oba robia to isté, len sa inak zobrazujú, rozdiel je v type písma, v jeho veľkosti a v riadkovaní
- `<polozka>` - obsahuje len text a je to element na zobrazenie ďalšej položky v jednom zo zoznamov
- `<obrazok>` - element na zobrazenie obrázka, musí obsahovať element `<zdroj>`
- `<video>` - element na zobrazenie videa v prehliadači, musí obsahovať element `<zdroj>`
- `<zdroj>` - obsahuje len názov súboru, ktorý je v priečinku `data`, toto smerovanie do priečinka `data` je vykonávané v šablóne, nie je potrebné zadávať absolútnu alebo relatívnu cestu, stačí názov súboru na zobrazenie
- `<typ>` - element na špecifikovanie typu videa, pre `.mp4` video je typ `video/mp4`
- `<p>` - štandardný element na odsek (resp. paragraph), musí obsahovať len text a môže mať jeden atribút - veľkosť písma v pixeloch, ak nie je atribút zadaný, je predvolene nastavená veľkosť písma na 20 px
- `<lava_strana>`, `<prava_strana>` - elementy na rozdelenie obrazovky na polovice, môžu obsahovať to isté čo element `<telo>`, len s tým rozdielom, že sa to zobrazí na príslušnej strane, použitie je výhodné vtedy, ak chceme do slajdu k textu pridať obrázok alebo video, pretože sa zobrazí na vyhradenej polovici obrazovky a text bude zalomený v ostatnej časti

&emsp;Ukážkovú XML prezentáciu je možné nájsť v súbore `source.xml`, tento dokument je valídny, overil som ho na [tejto](https://www.xmlvalidation.com) stránke.

&emsp;XSL transformácie som navrhol pre všetky elementy, parametrizovať je možné elementy `<p>`, `<titulok>` a `<zarovnaj>`. 
- `<nadpis>` a `<titulok>` sú písané štýlom Heading 1
- `<telo>` pred spracovním ďalších elementov zobrazí najskôr horizontálnu čiaru
- `<hruby_zoznam>` je písaný štýlom Heading 4 a veľkosťou písma 25px s riadkovaním 1,8
- `<zoznam>` je písaný štandardným písmom veľkosťou 20px, pokiaľ nie je zadaná iná veľkosť písma, a s riadkovaním 1,5
- na zalomenie častí slajdu v elementoch `<lava_strana>` a `<prava_strana>` sa využíva percentuálne rozloženie z CSS súboru
- v súbore s transformáciami je ako posledná uvedená transformácia s názvom `loop`, ktorá je takým automatizovaným "for-cyklom" na generovanie navigácie v spodnej časti slajdu s linkami na ostatné slajdy, resp. na ďalší/predchádzajúci slajd

&emsp;XSL transformácie môžete nájsť v súbore `sablona.xsl`. Do hlavičky každého `.xhtml` súboru sa vložia potrebné deklarácie, ako aj cesty k CSS štýlom, resp. súboru. Na "krajšie" zobrazenie používam voľne dostupný bootstrap, ktorý som si upravil pre potreby prezentácie a rozšíril o svoje ďalšie štýly (rozdelenie obrazoviek, formátovanie obrázka/videa, štýl liniek). Deklarácia týchto štýlov sa nachádza v súbore `my_css.css`. Každý slajd sa generuje do vlastného `.xhtml` súboru do priečinka `html_pages`. Obrázky a videá sa nachádzajú v priečinku `data`.

**Generovanie XHTML stránok**

Na generovanie som používal Saxon verzie 9 spolu so skriptom od kolegu. Saxonu sú dodané dva súbory - zdrojová XML prezentácia a súbor s XSL transformáciami. Na spustenie skriptu stačí mať skript, XML a XSL súbor v rovnakom priečinku, nasmerovať Terminál do tohto priečinka a už len zadať príkaz `make`.

**Štruktúra odovzdaného .zip archívu**

```
- css
	- my_css.css
- data
	- flaming.png 
	- IMG_1005.mp4
	- kybersikana.png
	- oko.png
	- ruleta.png
	- hadka.png
- html_pages
	- result_1.xhtml
	- result_2.xhtml
	- result_3.xhtml
	- result_4.xhtml
	- result_5.xhtml
	- result_6.xhtml
	- result_7.xhtml
	- result_8.xhtml
	- result_9.xhtml
- zdroje
	- makefile
	- sablona.xsl
	- source.xml
- _Z3-hoferica.txt
```
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