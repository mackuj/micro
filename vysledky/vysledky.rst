****************************
Výsledky
****************************


V této kapitole jsou popsány dosažené výsledky a možné praktické využití ročníkové práce Digitální zpracování mikroskopových obrazů.


================================
Hardwarová část
================================

V oblasti hardware jsem řešil několik problémů. 

Modul Picamera je k Raspberry Pi připojen pomocí speciálního plochého kabelu. Ten je však příliš krátký a navíc je náchylný k mechanickému opotřebení. Z důvodu, abych mohl využít plný rozsah zvětšení mikroskopu, rozhodl jsem se přilepit Raspberry Pi k tělu mikroskopu.

Ze začátku bylo téměř nemožné udržet kameru v přesné vzdálenosti a sklonu od okuláru. Proto jsem se rozhodl vytvořit "adaptér", který by držel kameru v přesné vzdálenosti od mikroskopu. Tento problém jsem řešil na několikrát a z toho důvodu je nádstavec poněkud nevzhledný, avšak funkční.

Díky těmto úpravám je mikroskop již zcela nezávislý a vyžaduje pouze minimální manipulaci.


================================
Softwarová část
================================

V oblasti software jsem řešil také několik problémů.

Bylo třeba vyřešit jakým způsobem budu komunikovat s modulem kamery. Toto jsem vyřešil pomocí pythonovské knihovny picamera, která byla k tomuto účelu vytvořena. Než jsem ji však mohl začít používat, musel jsem modul kamery povolit v základním nastavení Raspberry Pi.

Také jsem musel najít nějaký jednoduchý způsob jak fotografie upravovat. Vybral jsem si knihovnu Open-cv, která umí fotografie zpracovávat mnoha způsoby. Nastal však problém s její instalací, neboť není v základní nabídce pro Raspberry Pi a tak jsem musel knihovnu poměrně složitě instalovat z neoficiálního serveru.

Jedním z posledních problémů bylo vytvoření webové aplikace ve Flasku. Tato část byla programátorsky nejnáročnější. Bylo třeba předělat původní kód a naroubovat ho na společné prostředí pythonu a html. 

Ve výsledku tato aplikace funguje plynule a tak jak má.


================================
Praktické využití
================================

Můj digitální mikroskop má několik možností využití. Jakožto nízkonákladová úprava klasického optického mikroskopu může být používán zejména studenty při výuce. Ve školních laboratořích může být použit v biologii a chemii pro pořízení snímků vzorků nebo k počítání buněk a krystalů, v informatice pak k výuce Computer vision. 

Zde jsou ukázky z prostředí mé aplikace.

.. figure:: /images/appnormal.png
   :scale: 20%
   :alt: Aplikace s neupraveným snímkem.

   Aplikace s neupraveným snímkem.

.. figure:: /images/appsedy.png
   :scale: 20%
   :alt: Aplikace s černobílým snímkem.

   Aplikace s černobílým snímkem.


.. figure:: /images/appprah.png
   :scale: 30%
   :alt: Aplikace s vyprahovaným snímkem.

   Aplikace s vyprahovaným snímkem.

.. figure:: /images/appjas.png
   :scale: 30%
   :alt: Aplikace se zjasněným snímkem.

   Aplikace se zjasněným snímkem.

^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Obrázky z mikroskopu
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Následuje ukázka fotografií pořízených s pomocí mého digitálního mikroskopu. 


.. figure:: /images/phrot.jpg
   :scale: 20%
   :alt: Aplikace se zjasněmím snímkem.

   Vyprahovaný snímek trnu kaktusu.

.. figure:: /images/ccibule.jpg
   :scale: 20%
   :alt: Aplikace se zjasněmím snímkem.

   Neupravený snímek slupky cibule.
  
.. figure:: /images/sccibule.jpg
   :scale: 20%
   :alt: Aplikace se zjasněmím snímkem.

   Černobílý snímek  slupky cibule.

.. figure:: /images/pccibule.jpg
   :scale: 20%
   :alt: Aplikace se zjasněmím snímkem.

   Vyprahovaný snímek slupky cibule.

.. figure:: /images/jccibule.jpg
   :scale: 20%
   :alt: Aplikace se zjasněmím snímkem.

   Zjasněný snímek slupky cibule.

.. figure:: /images/cibule.jpg
   :scale: 20%
   :alt: Aplikace se zjasněným snímkem.

   Neupravený snímek cibule.
  
.. figure:: /images/scibule.jpg
   :scale: 20%
   :alt: Aplikace se zjasněmím snímkem.

   Černobílý snímek cibule.

.. figure:: /images/pcibule.jpg
   :scale: 20%
   :alt: Aplikace se zjasněmím snímkem.

   Vyprahovaný snímek cibule.







.. figure:: /images/vanocni.jpg
   :scale: 20%
   :alt: Aplikace se zjasněmím snímkem.

   Neupravený snímek listu vánoční hvězdy.





.. figure:: /images/svanocni.jpg
   :scale: 20%
   :alt: Aplikace se zjasněmím snímkem.

   Černobílý snímek vánoční hvězdy.


.. figure:: /images/jitka.jpg
   :scale: 20%
   :alt: Aplikace se zjasněmím snímkem.

   Neupravený snímek okvětního listu.

.. figure:: /images/pjitka.jpg
   :scale: 20%
   :alt: Aplikace se zjasněmím snímkem.

   Vyprahovaný snímek okvětního lístku.

.. figure:: /images/list.jpg
   :scale: 20%
   :alt: Aplikace se zjasněmím snímkem.

   Neupravený snímek listu.

.. figure:: /images/plist.jpg
   :scale: 20%
   :alt: Aplikace se zjasněmím snímkem.

   Vyprahovaný snímek listu.




