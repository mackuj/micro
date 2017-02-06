************************
Teoretický úvod
************************

.. |_| unicode:: 0xA0
   :trim:

V této kapitole se zaměřím na výklad některých základních pojmů, které souvisejí s mojí prací.


=======================
Digitální obraz
=======================

Digitální obraz je digitální (číselná) reprezentace obrazu, kterou používají počítače. Základní jednotkou obrázku je pixel (jeden bod). Tyto pixely jsou uspořádány do pravoúhlé matice. Pozice jednotlivých pixelů v matici je dána souřadnicemi x a y. Pozice 0,0 bývá  zpravidla v levém horním rohu obrazu. Pixel má několik vlastností, které určují kromě jeho pozice také barvu (většinou ve formátu RGB) a jas. Pro uložení obrazové matice do souboru se používají různé formáty. Ty se liší vnitřním uspořádáním a někdy způsobem komprese, která umožňuje zmenšit velikost souboru. Nejpoužívanější formáty jsou uvedeny v následující tabulce.


.. tabularcolumns:: |p{1.5cm}|p{4cm}|p{2cm}|p{6cm}|

.. list-table:: Formáty digitálních obrazů.
   :header-rows: 1

   * - Název
     - Komprese
     - Přípony 
     - Poznámka 
   * - JPEG
     - Ztrátová komprese
     - .jpg .jpeg
     - fotografie
   * - PNG
     - Bezztrátová komprese
     - .png
     - ikony, schémata, grafy 
   * - GIF
     - Bezztrátová komprese
     - .gif
     - stejné využití jako png, jednoduché animace
   * - BMP
     - Bez komprimace
     - .bmp
     - velmi jednoduchý


===========================
Digitální zpracování obrazu
===========================

Digitální zpracování obrazu je technická disciplína, jenž se zabývá zpracováním obrazových dat. Data mohou mít různý původ např. fotoaparát (digitální), kamera a nebo jiné obraz pořizující zařízení. Zpracování takto pořízeného digitálního obrazu může mít následující charakter:

* Zpracování za účelem zlepšení obrazu (jas, kontrast, barva, ostrost a podobně)
* Zpracování za účelem získání informací v obraze obsažené - takzvaný Computer vision


==========================
Computer vision
==========================

Computer vision je počítačové odvětví, které se zabývá zpracováním obrazu za jiným než jen vizuálním účelem. Tento obor se poprvé objevil v roce 1960. Toto téma také souvisí s umělou inteligencí, neboť se snaží, aby počítače vyhodnocovaly obrázky jako lidé (zpracovávaly jejich obsah). Je však velice těžké dosáhnout nějakého výsledku, který by se blížil lidskému zpracování vizuálních dat. Protože lidský mozek tato data zpracovává podvědomě a nesmírně složitě. Proto je vymýšlení a psaní algoritmů pro Computer vision velmi složité a náročné. Computer vision má velice široké využití, například:

* Kontrola výrobních procesů (kontroluje nezávadnost výrobků)
* V bezpečnosti (rozpoznávání obličejů, počítání lidí)
* K vytváření digitálních modelů (výrobní plány, mapy)
* Lékařské diagnostiky (z rentgenu, z magnetické rezonance)
* Na digitalizaci dat (ručně psané texty)


^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Kontrola výrobních procesů
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Moderní počítače již dnes dokáží dohlížet na sériovou výrobu. Například na tištěné spoje, které vyžadují velikou přesnost a i proto je lepší využít Computer vision, neboť v dlouhodobém horizontu dosahuje konstantnějších výsledků než lidské vidění.

^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Bezpečnost
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Computer vision má využití i v oblasti bezpečnosti. Může na kamerových záznamech zjišťovat a ověřovat identitu lidí porovnáním s databází. Toto může být využito buď na veřejných prostranstvích k rozpoznávání tváří u hledaných osob. Také se může využívat jako identifikační znak například v bance (obraz sítnice).

^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Digitální modely
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Computer vision se uplatňuje třeba i při vytváření modelů, map, 3D schémat, panoramatických obrázků a u mnoha dalších. Například u panoramatických obrázků se pomocí Computer vision hledají společné body. Poté se obrázky spojují za tyto body a následně je vytvořen jednolitý obraz. Všichni víme, že to není stoprocentní. Mohou při tom vznikat různé zlomy, záseky a  |_| všelijaké jiné deformace a to přesto, že program, který se na toto využívá je velice sofistikovaný a |_| komplikovaný.

^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Lékařské diagnostiky
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Toto odvětví najde využití také v medicíně. A to jako nástroj k určení diagnózy respektive léčby z obrazového materiálu. Například rentgenové snímky nebo obrazy z magnetické rezonance se zpracovávají za pomoci programů, které na základě porovnávání s databází podobných snímků dokážou určit místa, kde došlo k poranění. V tomto případě také v jistém smyslu nahrazují lidské oči, neboť ty mohou něco přehlédnout. Stále se však v této oblasti počítačům nevěří a |_| každý výsledek je pro jistotu kontrolován lékařem.

^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Digitalizace
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Pod funkce Computer vision patří také digitalizace. To se používá ku příkladu při zálohování psaných dokumentů a také z důvodu lepší dostupnosti. V takovém případě je text vyfotografován a poté pomocí Computer vision převeden na text (pomocí složitých vzorců) tato část Computer vision se nazývá OCR (optical character recognition). Takovýto text se samozřejmě kontroluje, jestli v něm není nějaká chyba (zvláště pak záleží na způsobu, jakým ho pisatel psal). 





