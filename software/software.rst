**********************************
Popis Software
**********************************

.. |_| unicode:: 0xA0
   :trim:


==============================
Použité softwarové prostředky
==============================


V této kapitole vysvětlím některé pojmy související s mojí prací a popíšu softwarovou část projektu, konkrétně:

* Programovací jazyk Python
* Knihovna Open-cv
* Knihovna picamera
* Flask


^^^^^^^^^^^^^^^^^^^^^^^^^^^
Programovací jazyk Python
^^^^^^^^^^^^^^^^^^^^^^^^^^^


.. index:: Python

Python je víceúčelový vysokoúrovňový skriptovací programovací jazyk. Byl vytvořen v roce 1991 Guido van Rossumem. Python je dostupný na většině operačních systémů a ve většině distribucí Linuxu je Python součástí základní dostupné instalace [#p1]_.  


.. figure:: /images/Python.png
   :scale: 12%
   :alt: Logo Python

   Logo programovacího jazyka Python.



Programovací jazyk Python vyniká zejména: 

* jednoduchou syntaxí - snadno se učí, je velice vhodný pro začátečníky
* univerzálností - lze použít jak pro krátké programy, tak i pro rozsáhlé aplikace
* obsáhlou nabídkou knihoven - umožňuje rychlý vývoj aplikací
* podporou objektového programování - není vyžadováno, programy ho nemusí využívat


Jako příklad kódu v různých programovacích jazycích se používá výpis známé věty *Hello World!* (Ahoj světe!). V Pythonu, jak je vidět, je to velice jednoduché.

.. code-block:: python

   # vypíše na obrazovku 
   print "Hello World!"

Python, narozdíl od jiných programovacích jazyků, vyžaduje *strukturované programování*. To znamená, že jednotlivé programové bloky musejí být náležitě odsazeny. To významně přispívá ke zpřehlednění a čitelnosti zápisu programu, jak je patrno na následující ukázce.

.. code-block:: python

   def priklad(text, podminka_text):
     """Příklad procedury pro výpis textu."""
     if podminka_text:
       print text
     else
       print "Žádný text."
     return  
   
   text = input("Zadejte text.")
   priklad(text, True)
   
Toto je ukázka vnořených struktur Pythonu.


Pro projekt Digitální zpracování mikroskopových obrazů jsem použil Python verze 2.7. Ve všech ukázkách kódu v této dokumentaci byla použita tato verze.

Většinu svých znalostí jazyka Python využitých v tomto projektu jsem  čerpal z knihy *Začínáme programovat v jazyce Python* (:cite:`2003:Harms`).


^^^^^^^^^^^^^^^^^^^^
Open computer vision
^^^^^^^^^^^^^^^^^^^^

.. index:: Open-cv

Open-cv je svobodná knihovna, umožňující zpracování digitálních obrazů. I když byla naprogramována v jazyku C++ je kompatibilní i s Pythonem a jednoduše se používá. Byla vyvinuta firmou Intel v roce 1999 a stále je vylepšována.


.. figure:: /images/ocv_logo.png
   :scale: 65%
   :alt: Logo knihovny Open-cv

   Logo knihovny Open-cv.


Ve své práci jsem využil pouze malou část jejích funkcí, přestože Open-cv má velice široké využití. Používá se například na: 

* převody mezi barevnými formáty (např. RGB na CMYK)
* vytváření histogramu
* prahování obrazu
* zaostřování obrazu
* geometrické transformace
* rozpoznávání vzorů
* a další


^^^^^^^^^^^^^^^^^^^^
Knihovna picamera
^^^^^^^^^^^^^^^^^^^^

.. index:: Knihovna picamera

Picamera je speciální knihovna mikropočítače Raspberry Pi, která je určena k ovládání kamery. Umožňuje většinu věcí jako normální fotoaparát. Můžete si nastavit samospoušť, snímat video, ostřit, měnit jas, měnit rozlišení a spoustu dalších nastavení. Já jsem však využil pouze funkce snímání jedné fotografie, a nastavení rozlišení.


^^^^^^^^^^^^^^^^^^^^
Flask
^^^^^^^^^^^^^^^^^^^^

.. index:: Flask

Flask je pythonovský mikroframework na tvorbu webových aplikací. Narozdíl od ostatních frameworků je velmi jednoduchý a přímočarý. Používá se pro vytváření jednoduchých webových aplikací. Jeho struktura využívá řadu hotových knihovních funkcí a umožňuje jednoduše přidávat další knihovny. 

Rychlý "přechod" mezi Pythonem a HTML zajišťuje použitý šablonovací modul Jinja rovněž napsaný v Pythonu. Flask zajišťuje oddělení vlastního výkonného kódu od html vzhledu a |_| usnadňuje tak soustředit se na vlastní problém.

Flask má výbornou dokumentaci (:cite:`2014:Grinberg`) a četnou komunitu, která usnadňuje začátečníkům život.


================================
Struktura Programu
================================

Práce s obrazy vyžaduje grafické uživatelské rozhraní. Nejjednodušší způsob jak vytvořit grafické rozhraní je použití webové aplikace. Pro vytvoření webové aplikace jsem použil rámec Flask. 

Struktura programu je určena požadavky rámce Flask, který odděluje výkonný kód od vzhledu. 

:: 

   run.py
   config.py
   instance/
     config.py
   app/
     __init__.py
     views.py
     models.py
     forms.py
     static/
       style.css
       script/
         jquery-2.1.3.js
         SimpleQueryDropdowns
      templates/
       base.html
       fun.html


Ve výše uvedené struktuře jsou nejdůležitější soubory:

* run.py - spouští webovou aplikaci, která běží na Raspberry Pi jako server.
* views.py - vlastní kód pro snímání a úpravu obrazů.  
* base.html - základní šablona v html
* fun.html - kód pro html zobrazení nasnímaných a upravených obrazů. Obsahuje vstupní body pro přenos dat mezi kódem ve views.py a výsledným html. 
* style.css - kaskádový styl
* SimpleQueryDropdowns - knihovna v javascriptu, pomocí které je vytvořeno nabídkové menu


Funkci běžící aplikace lze zjednodušeně znázornit na následujícím obrázku:

.. figure:: /images/schema.png
   :scale: 50%
   :alt: Blokové schéma aplikace

   Blokové schéma aplikace




====================================
Důležité funkční bloky
====================================

^^^^^^^^^
views.py
^^^^^^^^^

V souboru views.py jsou nadefinovány čtyři funkce pro jednotlivé druhy úprav. První je obyčejný snímek bez jakýchkoliv úprav. Druhým je černobílý snímek. Třetí je snímek vyprahovaný. A |_| poslední je snímek s upraveným jasem. Soubor *views.py* obsahuje vlastní výkonný kód aplikace. Hlavní část je tvořena čtyřmi funkcemi pro jednotlivé operace spouštěné z webového rozhraní. Každá z funkcí obsahuje sejmutí snímku kamerou pomocí knihovny picamera a následující úpravu sejmutého obrazu. Obraz se snímá do proměnné, která se používá jako zdroj dat pro funkce Open-cv provádějící zpracování. 


.. code-block:: python

  def sedy(resol, uloz):    
      """ Sejmutí obrazu ve stupních šedi """
      my_stream = BytesIO()   
      with picamera.PiCamera() as camera:
          camera.resolution = fnGetResol(resol)
          camera.capture(my_stream, format='jpeg')
          nparr = np.fromstring(my_stream.getvalue(), np.uint8)
          foto = cv2.imdecode(nparr, cv2.CV_LOAD_IMAGE_COLOR)
          sedyobr = cv2.cvtColor(foto, cv2.COLOR_BGR2GRAY)
          r, sedyobrb = cv2.imencode(".jpeg", sedyobr)
      if uloz == 'True':
         with open(fnGetFileName('sedy'), 'wb') as f:
             f.write(sedyobrb)
      return Response(bytearray(sedyobrb), mimetype='image/jpeg')
    
   
Toto je ukázka funkcí knihovny picamera.

^^^^^^^^^^
fun.html
^^^^^^^^^^

V HTML kódu je napsáno o zobrazování obrázku a o volání funkcí z views.py. 


.. code-block:: HTML

      <table>
        {% for subfield in form.resol %}
        <tr>
          <td>{{ subfield.label }}</td>
          <td>{{ subfield }}</td>
        </tr>
        {% endfor %}
        {% if funid == 4 %}
        <tr>
          <td>{{ form.hodnot.label }}</td> 
          <td>{{ form.hodnot(size="5", title="Zadejte desetinné číslo od 0 do 5 s desetinnou tečkou!") }}</td>
        </tr>
        {% endif %}
        <tr><td>&nbsp;</td><td>&nbsp;</td></tr>
        <tr>
          <td>{{ form.uloz.label }}</td> 
          <td>{{ form.uloz }}</td>
        </tr> 
      </table>

    
   
Toto je ukázka kódu ze souboru fun.html.


====================================
Aplikace
====================================

V této kapitole je uveden návod k použití aplikace.

^^^^^^^^^^^^^^^^^^^^^^^^^
Spuštění aplikace
^^^^^^^^^^^^^^^^^^^^^^^^^

Aplikace je webová a k jejímu zpřístupnění se používá webový prohlížeč. Aplikaci jsem ladil v |_| prohlížeči Firefox verze 50.1, měla by však fungovat v každém moderním prohlížeči (například Internet Explorer nebo Chrome). Aplikace se spustí zadáním následující adresy do adresového řádku prohlížeče.  

::

  http://malina04:5000/ 
 


Prostředí aplikace vypadá takto:

.. figure:: /images/prostredi.png
   :scale: 20%
   :alt: Prostředí aplikace.

   Prostředí aplikace.

Na obrázku 3.4 můžete vidět, jak vypadá aplikace hned po spuštění bez zvolené funkce.

^^^^^^^^^^^^^^^^^^^^^^^
Funkce
^^^^^^^^^^^^^^^^^^^^^^^

V horní liště se nachází nabídka pro volbu jednotlivých funkcí 

* Neupravený obrázek 
* Černobílý obrázek 
* Vyprahovaný obrázek 
* Obrázek se změněným jasem

Při výběru jedné z těchto funkcí se automaticky sejme obrázek, který se zobrazí v |_| pravé části plochy aplikace místo nápisu Digitální Mikroskop. Současně se změní levý panel, ve kterém se zobrazí možnosti dostupné pro zvolenou funkci.

.. figure:: /images/moznosti.png
   :scale: 50%
   :alt: Možnosti v aplikaci.

   Možnosti v aplikaci

Je zde možnost změny rozlišení mezi velké (2592, 1944) a malé (1024, 768). Když není vybrána ani jedna je rozlišení (1320, 990). Volbu je třeba potvrdit tlačítkem níže.

Výsledek zpracování funkcí se posílá prohlížeči. Uložení se provádí pouze, pokud je to požadováno uživatelem zvolením volby "Uložit". Obrázek můžete najít ve stejné složce jako soubory k aplikaci pod názvem: *název funkce (která byla použita) a datum s časem.jpg*

U funkce změny jasu se ještě objeví kolonka na zadání hodnoty, o kterou se změní jas (od 0 do 5 s použitím desetinné tečky).

.. figure:: /images/appsedy.png
   :scale: 35%
   :alt: Aplikace s černobílým snímkem.

   Aplikace s černobílým snímkem.


.. rubric:: Poznámky pod čarou

.. [#p1] Python je i součástí distribuce Raspbian, která se používá v Raspberry Pi.

