******************************
Popis Hardware
******************************

V této kapitole je popsán hardware, který jsem použil ve svém projektu. Zároveň jsou zde popsány principy na kterých můj digitální mikroskop funguje.

==============================
Raspberry Pi
==============================

.. index:: Raspberry Pi

.. |_| unicode:: 0xA0
   :trim:

Raspberry Pi je malý počítač s ARM procesorem, který byl vyvinut se záměrem vzbudit u dětí a |_| mládeže zájem o programování. Krátce po jeho uvedení na trh se však vytvořila velká komunita uživatelů, kteří Raspberry Pi používají jako univerzální počítač pro nejrůznější projekty. K |_| jednoduché komunikaci slouží GPIO sběrnice, jejíž součástí je i I2C sběrnice. Na Raspberry Pi se dá připojit velké množství doplňků například pi camera. Dále obsahuje HDMI konektor k připojení na monitor, nebo televizi a také USB a ethernetový adaptér. Pevný disk je nahrazen SD kartou, na které je uložen jak operační systém, tak uživatelská data. V mém projektu je využito Raspberry Pi 2 Model B.

.. tabularcolumns:: |p{2.5cm}|p{7cm}|p{5cm}| 

.. list-table:: Technické parametry Raspberry Pi 2 model B
   :header-rows: 1

   * - Parametr
     - Hodnota
     - Poznámka  
   * - Rozměry
     - 85.60 mm × 56.5 mm
     - 
   * - Paměť RAM 
     - 1 GB
     - Sdíleno s grafickou kartou 
   * - Procesor
     - ARMv7 
     - ARM Cortex-A7 (4 jádro)
   * - Frekvence
     - 900 MHz
     - 
   * - Porty 
     - 4x USB, 1x ethernet, 1x HDMI, 1x 3,5 mm audio, 1x composite video
     - 
   * - Napájení
     - 5 V, 700 mA
     - konektor micro USB



.. figure:: /images/Raspberry-Pi-2-model-b.jpg
   :scale: 100%
   :alt: Obrázek Raspberry pi.

   Minipočitač Raspberry Pi 2 použitý v tomto projektu.

Narozdíl od Raspberry Pi 1 model B je model 2 B asi 6x výkonnější. Tento výkon je využit hlavně při zpracování nasnímaných obrazů, které je obecně výkonově náročné.


==============================
Pi camera
==============================

.. index:: Pi camera

Použil jsem modul Pi camera, který je kompatibilní s mikro počítačem Raspberry Pi. Tato kamera dokáže nahrávat jak video, tak jednotlivé fotky. Navíc má malou čočku, takže se dá nasadit na okulár mikroskopu, aniž by byla fotka příliš oříznuta. 


.. figure:: /images/Picamera.jpg
   :scale: 25%
   :alt: Obrázek Picamery.

   Modul kamery k Raspberry Pi.



==============================
Mikroskop
==============================

.. index:: Mikroskop

Ve svém projektu jsem použil již trochu starší Kleinmikroskop typu C od firmy ROW Ratenow s maximálním zvetšením 225×, bez umělého zdroje světla.

Mikroskop se používá ke zkoumání mikro světa (což je obsaženo v jeho názvu), od hmyzu, až po stavbu látek. Funguje na optickém principu ohýbání světla. 

První funkční mikroskop byl sestaven Nizozemcem Zacharisem Janssenem v roce 1590. Většina mikroskopů se skládá ze dvou částí. První částí je složitá soustava čoček, druhou pak mechanická, podpěrná konstrukce a zaostřování.

.. figure:: /images/Mikroskop.jpg
   :scale: 10%
   :alt: Obrázek Mikroskopu Kleinmikroskop C.

   Optický mikroskop Kleinmikroskop C použitý v tomto projektu.


Výsledná sestava "digitálního" mikroskopu vznikla za pomoci oboustranné lepicí pásky, která přidržuje Raspberry Pi na těle mikroskopu. Mezikus mezi okulárem a kamerou je tvořen dřevěnou destičkou a plastovou podložkou, které jsou spojeny opět oboustrannou lepící páskou. Tento způsob propojení jednotlivých částí je dočasný, pro případ trvalého používání by bylo nutno zvolit jiné řešení zejména u spojení kamery s okulárem. 




.. figure:: /images/sestava.JPG
   :scale: 35%
   :alt: Obrázek mého mikroskopu.

   Mikroskop s Raspberry Pi a kamerou.



^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Vzorky
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Proto, abych mohl demonstrovat funkčnost svého digitálního mikroskopu, potřebuji samozřejmě nějaké vzorky na pozorování. Jako vzorky jsem použil šest rostlinných látek a lidský vlas.

Vzorky jsou zleva:

* okvětní plátek květiny Crossandra Fortuna
* slupka z červené cibule
* vnitřní slupka cibule
* list Pryšce nádherného (zvaný vánoční hvězda)
* lidský vlas
* list květiny Crossandra Fortuna
* trn z kaktusu


Vzorky jsou vyrobeny tradičním způsobem. Na podkladové sklíčko, umístíme pozorovaný preparát, který se překryje krycím sklíčkem. Pro identifikaci je třeba opatřit vzorek popiskem.



.. figure:: /images/vzorky.JPG
   :scale: 50%
   :alt: Obrázek vzorků.

   Obrázek se vzorky použitými v projektu.















