---
icon: material/numeric-4-box
title: Cvičení 4
---
# Georeferencování, editace a tvorba vektorových dat

## Georeferencování
Rastrová data pocházejí z různých zdrojů, například z družicových snímků, leteckých snímků nebo skenovaných map. Zatímco moderní družicové a letecké snímky obvykle obsahují poměrně přesné informace o své poloze a pro správné zobrazení společně s ostatními daty GIS mohou vyžadovat pouze drobné úpravy, skenované mapy a historické podklady zpravidla žádnou informaci o prostorovém umístění neobsahují. V takových případech je nutné provést georeferencování.

Georeferencování je proces přiřazení skutečných geografických souřadnic rastrovému obrazu nebo skenované mapě, který umožňuje jejich správné umístění v souřadnicovém referenčním systému. Spočívá ve vyhledání totožných, jednoznačně identifikovatelných bodů na georeferencovaném obrazu a na referenčních datech, například družicovém snímku či vektorové mapě. Jako vlícovací body je vhodné vybírat stabilní a snadno rozpoznatelné objekty v obou podkladech, například kostely, mosty, křižovatky, soutoky řek nebo dlouhodobě existující veřejné budovy. Body by měly být rozmístěny po celé ploše mapového listu, nikoli soustředěny pouze do jednoho rohu.

Georeferencování má v kartografii a GIS zásadní význam, protože umožňuje propojit historické mapy, letecké snímky a další prostorová data s ostatními vrstvami GIS a využívat je k analýzám, vizualizacím a rozhodování.


<figure markdown>
  ![Georeferencování staré mapy](../assets/cviceni4/GeoreferencingMap.png "Georeferencování staré mapy"){ width=600px }
  <figcaption>Georeferencování staré mapy</figcaption>
</figure>


__Zdroje:__
{: align=center }

[<span>pro.arcgis.com</span><br>Přehled georeferencování](https://pro.arcgis.com/en/pro-app/latest/help/data/imagery/overview-of-georeferencing.htm){ .md-button .md-button--primary .server_name .external_link_icon_small target="_blank"}
[<span>pro.arcgis.com</span><br>Principy georeferencování rastrů](https://www.esri.com/about/newsroom/arcuser/understanding-raster-georeferencing/){ .md-button .md-button--primary .server_name .external_link_icon_small target="_blank"}
[<span>pro.arcgis.com</span><br>Nástroje pro georeferencování](https://pro.arcgis.com/en/pro-app/latest/help/data/imagery/georeferencing-tools.htm){ .md-button .md-button--primary .server_name .external_link_icon_small target="_blank"}
[<span>Brad Skopyk</span><br>Georeferencování historických map](https://storymaps.arcgis.com/stories/dd75d0398f7d4ded924d303161895b8b){ .md-button .md-button--primary .server_name .external_link_icon_small target="_blank"}
[<span>learn.arcgis.com/</span><br>Georeferencování historických snímků v ArcGIS Pro](https://learn.arcgis.com/en/projects/georeference-imagery-in-arcgis-pro/){ .md-button .md-button--primary .server_name .external_link_icon_small target="_blank"}
{: .button_array}

<hr class="level-1">

## Vektorizace

Pro analýzu rastrových map je téměř vždy nutné provést jejich vektorizaci, tedy převést obsah mapy na vektorová data. Existují různé možnosti automatizace tohoto procesu, zde si však ukážeme nejjednodušší metodu – ruční vektorizaci.


**1.** Nástroje pro editaci vektorových dat se nacházejí na kartě *:material-tab: Edit*{: .outlined_code}.

**2.** Nové prvky vytvoříte kliknutím na *:material-button-cursor: Create*{: .outlined_code} a následným výběrem kreslicího nástroje pro požadovaný podtyp v panelu *:material-tab: Create Features*{: .outlined_code}.

**3.** Při vektorizaci přidáváte jednotlivé vrcholy levým tlačítkem myši. Vektorizaci konkrétního prvku dokončíte dvojklikem levého tlačítka nebo výběrem ikony *:material-button-cursor: Finish*{: .outlined_code} mezi nástroji ve spodní části obrazovky. Při vektorizaci se ujistěte, že je zapnuté přichytávání [_:material-button-cursor: Snapping_{: .outlined_code}](https://pro.arcgis.com/en/pro-app/latest/help/editing/enable-snapping.htm).

**4.** Po dokončení editace vektorových dat nezapomeňte uložit změny kliknutím na *:material-button-cursor: Save*{: .outlined_code} na kartě *:material-tab: Edit*{: .outlined_code}.

<figure markdown>
![vektorizace](../assets/cviceni6/vekt.png)
    <figcaption>Vektorizace rastrové mapy</figcaption>
</figure>

__Zdroje:__
{: align=center }

[<span>pro.arcgis.com</span><br>Editace v ArcGIS Pro](https://pro.arcgis.com/en/pro-app/latest/help/editing/overview-of-desktop-editing.htm){ .md-button .md-button--primary .server_name .external_link_icon_small target="_blank"}
[<span>John Nelson</span><br>Rychlá a jednoduchá tvorba podrobných polygonů v ArcGIS Pro](https://youtu.be/Ab9aqsHj8X8?si=C4CCfrIkuYrrwDoK){ .md-button .md-button--primary .server_name .external_link_icon_small target="_blank"}
[<span>learn.arcgis.com</span><br>Kopírování prvků mezi vrstvami](https://learn.arcgis.com/en/projects/copy-features-between-layers/){ .md-button .md-button--primary .server_name .external_link_icon_small target="_blank"}
[<span>pro.arcgis.com</span><br>Úvod do podtypů (subtypes)](https://pro.arcgis.com/en/pro-app/latest/help/data/geodatabases/overview/an-overview-of-subtypes.htm){ .md-button .md-button--primary .server_name .external_link_icon_small target="_blank"}
[<span>University of Redlands</span><br>Návod pro ArcGIS Pro: georeferencování a digitalizace historické mapy indiánského teritoria Oklahoma](https://www.youtube.com/watch?v=QWv5nwCeZjA){ .md-button .md-button--primary .server_name .external_link_icon_small target="_blank"}
[<span>ArcGIS Blog</span><br>Digitalizace skenovaných map pomocí AI v ArcGIS Pro](https://www.esri.com/arcgis-blog/products/arcgis-pro/mapping/digitizing-scanned-maps-using-ai-in-arcgis-pro){ .md-button .md-button--primary .server_name .external_link_icon_small target="_blank"}
{: .button_array}

<hr class="level-1">

## Kontrola topologie vektorových dat

Chcete-li zkontrolovat topologickou správnost vektorových dat, musí být všechny vrstvy určené ke kontrole uloženy v jednom společném datasetu.

**1.** Novou topologii vytvoříte kliknutím pravým tlačítkem na dataset → *:material-form-dropdown: New*{: .outlined_code} → *:material-form-dropdown: Topology*{: .outlined_code}.

**2.** Na první stránce průvodce *:material-tab: Create Topology Wizard*{: .outlined_code} nastavte parametry topologie: její název, toleranci shlukování (cluster tolerance) / přesnost a vstupní vrstvy.

**3.** Na druhé stránce se definují topologická pravidla, která se mají kontrolovat. Nastavte je podle potřeby. V tomto příkladu ověříme pravidla *:material-magnify: Must Not Have Gaps (Area)*{: .outlined_code} (data nesmějí obsahovat mezery), *:material-magnify: Must Not Overlap With (Area-Area)*{: .outlined_code} (vrstvy se nesmějí vzájemně překrývat) a *:material-magnify: Must Not Overlap (Area)*{: .outlined_code} (prvky jedné vrstvy se nesmějí vzájemně překrývat).

**4.** Na třetí stránce se zobrazí souhrn nastavení topologie. Pro její vytvoření klikněte na *:material-button-cursor: Finish*{: .outlined_code}.

**5.** Pokud se topologie nezobrazí ve výstupním datasetu, aktualizujte jeho obsah kliknutím pravým tlačítkem → *:material-form-dropdown: Refresh*{: .outlined_code}.

**6.** Následně je nutné topologii zkontrolovat. V panelu *:material-tab: Catalog*{: .outlined_code} klikněte pravým tlačítkem na topologii → *:material-button-cursor: Validate*{: .outlined_code}.

**7.** Po kontrole přetáhněte vrstvu topologie do mapového okna. Měly by se zobrazit případné zjištěné chyby.

**8.** Pomocí nástrojů na kartě *:material-button-cursor: Edit*{: .outlined_code} opravte zvýrazněné chyby v původních datech. Po editaci topologii znovu zkontrolujte. Pokud nebyly nalezeny žádné chyby, jsou kontrolované vrstvy topologicky správné.


???+ note " <span style="color:#448aff">Tipy pro urychlení kontroly topologie:</span>"
    - U dat se stejnou hodnotou atributu (např. les, louka) můžete podle potřeby použít nástroj [*:material-cog: __Dissolve__*{: .outlined_code}](https://pro.arcgis.com/en/pro-app/latest/tool-reference/data-management/dissolve.htm). Ten sloučí prvky a může odstranit problémy se vzájemnými překryvy prvků stejné kategorie (například dvou překrývajících se polygonů luk).
    - Pro zjednodušení kontroly topologie můžete všechna kontrolovaná data sloučit do jedné vrstvy a následně kontrolovat pouze tuto vrstvu. Nebude tak nutné ověřovat překryvy mezi různými vrstvami pomocí pravidla :material-magnify: Must Not Overlap With{: .outlined_code}; místo toho budete kontrolovat pouze vzájemné překryvy prvků uvnitř nové vrstvy pravidlem :material-magnify: Must Not Overlap{: .outlined_code}. Po kontrole však nezapomeňte opravit nalezené chyby také v původních datech.

__Zdroje:__
{: align=center }

[<span>pro.arcgis.com</span><br>Co je topologie](https://pro.arcgis.com/en/pro-app/latest/help/data/topologies/an-overview-of-topology-in-arcgis.htm){ .md-button .md-button--primary .server_name .external_link_icon_small target="_blank"}
[<span>pro.arcgis.com</span><br>Schéma topologických pravidel](https://pro.arcgis.com/en/pro-app/latest/help/editing/pdf/topology_rules_poster.pdf){ .md-button .md-button--primary .server_name .external_link_icon_small target="_blank"}
{: .button_array}

<hr class="level-1">

## Úloha 03
!!! abstract "Vektorizace staré mapy"
    **ZADÁNÍ:**

    Vytvořte jednoduchou mapu rekonstruující část Prahy na počátku 20. století. V mapě rozlište alespoň čtyři typy prvků: vodní plochy, zeleň, zastavěné plochy a veřejná prostranství/ulice. Mapa musí obsahovat popisky alespoň jednoho prvku z každé kategorie, přičemž jejich grafická úprava musí odpovídat typu prvku.


    <br>
    **ZDROJE DAT:**
    
      [:material-map: Plán Prahy (1920–1930)](../assets/cviceni4/Prague_Plan_1920-1930_detail.jpg){ .md-button .md-button--primary .button_smaller target="_blank"}
      {: .button_array style="justify-content:flex-start;"}

    - Kde lze najít další staré mapy?

    [OldMapsOnline](https://www.oldmapsonline.org/){ .md-button .md-button--primary .server_name .external_link_icon_small target="_blank"}
    [David Rumsey Map Collection](https://www.davidrumsey.com/){ .md-button .md-button--primary .server_name .external_link_icon_small target="_blank"}
    {: .button_array}
    
    <br>
    **FORMA ODEVZDÁNÍ:**

    - 1 mapa ve formátu PDF (odevzdejte do 29. 3. na adresu <a href="mailto:petra.justova@fsv.cvut.cz">petra.justova@fsv.cvut.cz</a>)

    
    <div class="annotate" markdown>
    <br>
    **POSTUP:**
    
    **Krok 1:** **Georeferencování mapy**

    - Vytvořte nový projekt v ArcGIS Pro (uložte na disk H:).
    - Přidejte starou mapu do svého mapového projektu (*Map*) pomocí nástroje _Add Data_.
    - Vyhledejte přidanou mapu pomocí _Zoom To Layer_.
    - Aktivujte nástroj *Georeference* (karta *Imagery* → _Georeference_).
    - Na kartě *Georeference* klikněte na *Add Control Points*. Pokuste se najít alespoň 4 totožné body (vlícovací body) na georeferencovaném obrázku *(source)* a na referenční mapě *(target)*. Body by měly být rozmístěny po celé ploše obrázku, aby bylo dosaženo co nejlepšího prostorového umístění (například kostely, staré mosty, ostrovy, věže apod.).
    - Po zadání všech bodů klikněte na kartě *Georeference* na *Save* a následně na _Close Georeference_.

    **Krok 2:** **Tvorba nových dat**

    - Vytvořte nový dataset _(Catalog–Geodatabase–New–Dataset)_.
    - Vytvořte novou třídu prvků *(Catalog–Geodatabase–New–Feature Class)*. Založte dvě polygonové vrstvy: (1) první vrstva s názvem „extent“ bude vymezovat hranici zájmového území; (2) druhá vrstva s názvem „LandUse“ bude obsahovat vektorizované polygony jednotlivých typů využití území.
    - Pro vrstvu „LandUse“ vytvořte podtypy _(Attribute Table–Table–Add–Subtypes–Create)_. Definujte tyto podtypy: _Important building_ (významná budova), _Building_ (budova), _Public space/Street_ (veřejné prostranství/ulice), _Green area_ (zeleň), _Water body_ (vodní plocha) a _Other_ (ostatní).
    - Nastavte symbologii vrstvy „LandUse“ podle podtypů _(Save–Symbology–Unique Values)_ a přiřaďte jim barvy.
    - Vektorizujte hranici zájmového území do vrstvy „extent“.
    - Pomocí jednoduchých editačních nástrojů vektorizujte všechny typy využití území ve zvolené oblasti do vrstvy „LandUse“.
    - Sloučte prvky stejného podtypu do jednoho prvku _(Tools–Dissolve)_.
    - Nezapomeňte zkontrolovat topologii. V případě potřeby opravte nalezené chyby.
    - Vytvořte novou anotační vrstvu. V ní definujte čtyři anotační třídy, které budou odlišovat popisky čtyř základních kategorií využití území různým stylem písma a barvou, například: budovy (tučné písmo, černá/tmavě šedá), veřejná prostranství/ulice (běžné písmo, černá/tmavě šedá), zeleň (běžné písmo, tmavě zelená) a vodní plochy (kurzíva, tmavě modrá).
    - Popište alespoň jeden prvek z každé kategorie.

    **Krok 3:** **Tvorba mapového výstupu**

    - Vytvořte nové *Layout* (A4 na šířku – *Landscape*).
    - Doplňte název mapy.
    - Vložte mapové pole v měřítku 1 : 5 000.
    - Doplňte údaj o měřítku.
    - Doplňte informaci o autorovi.
    - Přidejte legendu pomocí _(Add Legend–Convert to Graphics–Ungroup)_ a upravte ji.
    - Zkuste přidat popisky některých významných míst.
    - Exportujte *Layout* do formátu PDF s rozlišením 120 DPI.

    </div>

<figure markdown>
  ![Ukázka výstupu](../assets/cviceni4/old_prague.png "Ukázka výsledného výstupu."){ width=800px }
  <figcaption>Ukázka výsledného výstupu.</figcaption>
</figure>


<!--
## Úloha 03
!!! abstract "Urbanistický vývoj města"
    **ZADÁNÍ:**

    Vytvořte mapu znázorňující urbanistický vývoj vybraného města (například vašeho rodného města, hlavního města vaší země apod.). Ze starých map odvoďte rozsah zastavěných ploch (pokuste se zachytit alespoň tři časová období včetně současnosti). Změnu se pokuste kvantifikovat v absolutních i relativních hodnotách.

    <br>
    V technické zprávě odpovězte na následující otázku:
    
    - Jak se během sledovaného období změnil rozsah zastavěné plochy (relativně i absolutně)?


    <br>
    **ZDROJE DAT:**
    
      [:material-map: Plán Prahy (1920–1930)](../assets/cviceni4/Prague_Plan_1920-1930_detail.jpg){ .md-button .md-button--primary .button_smaller target="_blank"}
      {: .button_array style="justify-content:flex-start;"}
    
    <br>
    **FORMA ODEVZDÁNÍ:**

    - Technická zpráva a 1 mapa ve formátu PDF (odevzdejte do 23. 3. na adresu <a href="mailto:petra.justova@fsv.cvut.cz">petra.justova@fsv.cvut.cz</a>)
    
    <div class="annotate" markdown>
    <br>
    **POSTUP:**
    
    **Krok 1:** **Vyhledání mapy**
    
    - V internetovém prohlížeči nebo digitálních mapových sbírkách vyhledejte starou mapu zvoleného města. <br>
    *(Pokud najdete již georeferencovanou mapu poskytovanou prostřednictvím služby [WMS/WMTS]("Web Map Service (WMS) a Web Map Tile Service (WMTS) jsou standardní protokoly pro poskytování prostorových dat jako mapových obrazů (např. PNG, JPEG) po internetu. Umožňují klientům načítat a zobrazovat mapy a mapové vrstvy ze serveru."), připojte ji k ArcGIS Pro __(1)__{title="Postup připojení služby WMS/WMTS k ArcGIS Pro"} a přejděte ke kroku 3.)*

    [OldMapsOnline](https://www.oldmapsonline.org/){ .md-button .md-button--primary .server_name .external_link_icon_small target="_blank"}
    [David Rumsey Map Collection](https://www.davidrumsey.com/){ .md-button .md-button--primary .server_name .external_link_icon_small target="_blank"}
    {: .button_array}


    - Pokud chcete použít jiný (starší) plán Prahy, můžete využít [:material-map: Jüttnerův plán Prahy (1816)](https://geoportalpraha.cz/en/data-and-services/5374334f2c8c446996a174cef7351310){ .md-button .md-button--primary .button_smaller }
    <br>
    *(Jüttnerův plán Prahy (1816) je již georeferencovaný a poskytovaný prostřednictvím [služby ArcGIS REST]("ArcGIS REST Service je webová služba, která umožňuje přístup ke geografickým datům a funkcím GIS prostřednictvím rozhraní REST. Umožňuje dotazování, vizualizaci a analýzu prostorových dat ze serveru ArcGIS Server v aplikacích a webových mapách."), stačí zkopírovat URL a přidat mapu do ArcGIS Pro __(2)__{title="Postup přidání dat pomocí cesty"} a přejít ke kroku 3.)*
        
    <br>
    **Krok 2:** **Georeferencování mapy**

    - Přidejte starou mapu do svého mapového projektu (*Map*).
    - Správně nastavte souřadnicový referenční systém mapy (*Properties–Coordinate Systems*).
    - Aktivujte nástroj *Georeference* (karta *Imagery*).
    - Přibližte si zájmové území (oblast zachycenou na staré mapě). Aktuální pohled uložte do *Bookmarks* (karta *Map*).
    - Na kartě *Georeference* zvolte *Fit to Display*, čímž obraz přibližně umístíte do aktuálního mapového pohledu. Pomocí nástrojů *Move/Scale/Rotate* můžete jeho polohu dále upřesnit, aby bylo v následujícím kroku snazší identifikovat vlícovací body.
    - Na kartě *Georeference* klikněte na *Add Control Points*. Najděte alespoň 4 totožné body (vlícovací body) na obrázku *(source)* a na referenční mapě *(target)*. Body by měly být rozmístěny po celé ploše obrázku, aby bylo dosaženo co nejlepšího umístění.
    - Po zadání všech bodů klikněte na kartě *Georeference* na *Save*.

        <br>
    **Krok 3:** **Vektorizace**

    - Vytvořte novou třídu prvků *(Catalog–Databases–New–Feature Class)*. Zvolte typ geometrie, přidejte atributová pole, která chcete evidovat *(„year“)*, a vyberte správný souřadnicový systém.
    - Vektorizujte rozsah zastavěných ploch ze všech georeferencovaných map (*Edit–Features–Create Feature*). Ke každému polygonu, odpovídajícímu jedné staré mapě, zadejte hodnotu atributu *„year“*.
    - Vhodně nastavte symbologii vrstvy tak, aby znázorňovala rozšiřování zastavěného území města *(Symbology–Graduated Colors)*. Vrstvy zobrazte nad referenční mapou zachycující současný rozsah zastavěných ploch *(Map–Layer–Basemap)*.
    - Dokončete mapovou kompozici: vložte název mapy (*Map Title*), měřítko (*Scale*), legendu (*Legend*) a údaje o zdrojích a autorech (*Credits*). Pokuste se vytvořit přehledný a estetický výstup. Inspiraci najdete na ukázce níže. <br>
    - Exportujte *Layout* do formátu PDF.

    </div>

    1.  ![](../assets/cviceni4/ServerConnection.png){ .no-filter width=700px} Přidání služby WMS/WMTS do ArcGIS Pro
    2.  ![](../assets/cviceni4/AddDataFromPath.png){ .no-filter width=700px} Přidání dat do ArcGIS Pro pomocí cesty

    <br>
    ![](../assets/cviceni4/PragueMap.png){ width=600px }
    {: align=center}

-->
