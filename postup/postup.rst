****************************
Postup
****************************

.. |_| unicode:: 0xA0
   :trim:

=============================
Výběr komponentů
=============================

Na projektu jsem pracoval od září 2016. Pro svůj projekt jsem znovu vybral mikropočítač Raspberry Pi, který jsem použil už ve své minulé práci Tweetující rostlina ( http://mujweb.cz/playback/kytkajitka/html/ ). Poté jsem zjišťoval možnosti zařízení Pi camera, které je kompatibilní s Raspberry Pi. Poté jsem přešel k výběru vhodného programovacího jazyka pro svůj program a rozhodl jsem se znovu pro jazyk Python. Jako pomocný nástroj pro zpracování obrazového výstupu z kamery jsem vybral knihovnu Open-cv, která je z důvodu rychlosti napsaná v jazyce C++, umožňuje však jednotlivé funkce volat z jazyka Python. Knihovna je velmi rozsáhlá a kromě funkcí, které jsem použil ve své aplikaci obsahuje mnoho dalších. Jako mikroskop jsem využil optický mikroskop Kleinmikroskop typu C od firmy ROW Ratenow s |_| maximálním zvetšením 225×. Ten jsem dostal už před mnoha lety. 

===========================
Vývoj hardware
===========================

K mikroskopu jsem oboustrannou lepicí páskou přilepil mikropočítač Raspberry Pi umístěný do krabičky typu Onenine. Kameru jsem připojil pomocí speciálního plochého kabelu. Kamera je následně přidržována na okuláru mikroskopu pomocí nádstavce složeného z dřevěné a dvou dalších plastových destiček, které jsou pohromadě drženy znovu oboustrannou lepicí páskou. Připevnění kamery k okuláru bylo náročné, protože na správném umístění kamery závisí kvalita nasnímaných obrazů. Kamera musí být umístěna v optické ose a současně ve správné vzdálenosti od čočky okuláru. Proto jsem postupně přidával plastové destičky, až bylo dosaženo odpovídající kvality obrazu.

===========================
Vývoj software
===========================

Při programování jsem nejdříve zprovoznil komunikaci s kamerou a ukládání obrazů. Poté jsem připojil jednoduché funkce na úpravu obrazu z knihovny Open-cv. Následovalo skloubení všech funkcí do prvního programu a vytvoření psaného menu v terminálu. To však bylo nedostačující a tak jsem se začal zabývat vytvářením aplikace ve Flasku.

Zde nastal problém v tom, že program neukazoval aktuální obrázek, ale první pořízený protože prohlížeč využívá cache pro zrychlení, což v tomto případě bylo nežádoucí. To jsem nakonec vyřešil tím, že jsem obraz nesnímal rovnou do obrázku, ale jako datový stream. Problém se zobrazováním sice zmizel, avšak objevil se nový a to ten, že předem naprogramované funkce již nefungovaly a tak jsem je musel upravit. To se podařilo a zbývalo jen dodělat ukládání a změnu jasu. Přesto, že bylo všechno hotovo, strávil jsem ještě mnoho času vytvářením dokumentace.


