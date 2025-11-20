# Semestrální práce – Analýza území

## Zadání

Připravte tištěný mapový poster či webovou mapovou aplikaci, který/á se bude věnovat analýze území dané ORP (viz níže) s ohledem na vhodnost stavby tří objektů:

- nová **solární elektrárna** :material-solar-power-variant:{ .lg .middle } ,
- nová **rozhledna** :material-tower-fire:{ .lg .middle },
- nová **skládka** :material-dump-truck:{ .lg .middle }.


??? task-fg-color "Individuální zadání"
    <iframe src="https://docs.google.com/spreadsheets/d/e/2PACX-1vQfN5ojqTC5jXvkKUlyuNzHbgnunUQHZ2tbxWmFeYRKKgx-a3Mq3v2FXlNcAX9ebQ/pubhtml?gid=967359062&single=true" width="100%" height="300" frameBorder="0"></iframe>


<hr class="level-1">
<div class="annotate" markdown>
### :material-solar-power-variant:{ .lg .middle } **SOLÁRNÍ ELEKTRÁRNA**

V zadaném ORP identifikujte **vhodné plochy pro výstavbu solární elektrárny**{style="text-transform:uppercase;"}.

Při analýze zohledněte následující hodnoticí kritéria:

- :material-slope-uphill:{ .lg .middle } **Sklonitost svahu:** Pro instalaci solárních panelů jsou vhodné zejména rovinaté nebo mírně svažité terény.

<div style="text-align:center;" markdown>

| Sklonitost | Bodové ohodnocení  |
|---|---------------------------|
| 0–1° | 3 |
| 1–4° | 2 |
| 4–7° | 1 |
| >7° | 0 |

</div>

- :material-sun-angle:{ .lg .middle } **Orientace svahu:** Pro instalaci solárních panelů jsou vhodné zejméne plochy orientované na jih, jihovýchod nebo jihozápad.

<div style="text-align:center;" markdown>

| Orientace svahu | Bodové ohodnocení  |
|---|---------------------------|
| azimut 0°–112,5° | 0 |
| azimut 112,5°–135° (VJV-JV)| 1 |
| azimut 135°–157,5° (JV-JJV) | 2 |
| azimut 157,5°–202,5° (JJV-J-JJZ) | 3 |
| azimut 202,5°–225°  (JJZ-JZ)| 2 |
| azimut 225°–247,5° (JZ-ZJZ) | 1 |
| azimut 247,5°–360° | 0 |

</div>

- :material-island-variant:{ .lg .middle } **Typ využití půdy:** Pro výstavbu solární elektrárny jsou vhodné např. trvalé travní porosty, solární elektrárnu je však možné vybudovat i na orné půdě. 

<div style="text-align:center;" markdown>

| Typ využití půdy | Bodové ohodnocení  |
|---|---------------------------|
| louka, trvalý travní porost | 3 |
| orná půda   | 1 |
| ostatní typy | 0 |

</div>


Plocha pro výstavbu solární elektrárny je považována za vhodnou, pokud má **rozlohu více než 1 ha** a její celkové bodové ohodnocení dosahuje **min. 7 bodů**.

Z výsledků analýzy vyberte **3 nejvhodnější lokality pro výstavbu solární elektrárny**{style="text-transform:uppercase;"} dle jejich celkové rozlohy a bodového ohodnocení. Ve finálním výběru prioritizujte lokality, které mají nejvyšší bodové ohodnocení. 

Vytvořte přehlednou vizualizaci zobrazující vybrané lokality. Ve výsledné vizualizaci uveďte pro jednotlivé lokality následující atributy: plocha v hektarech, celkové bodové ohodnocení.


- **DATOVÉ ZDROJE:**

    [:material-layers: DMR5G ](https://ags.cuzk.gov.cz/arcgis2/rest/services/dmr5g/ImageServer){ .md-button .md-button--primary .button_smaller target="_blank"}
    [:material-layers: ZABAGED ](https://ags.cuzk.gov.cz/arcgis/rest/services/ZABAGED_POLOHOPIS/MapServer " ''Orná půda a ostatní dále nespecifikované plochy', 'Trvalý travní porost'' "){ .md-button .md-button--primary .button_smaller target="_blank"}
    {: .button_array style="justify-content:flex-start;"}


???+ task-fg-color "Jak na to?"
    
    1. připravte si DMR5G pro své území
        - *Add Data From Path* --> *Data-Export Raster* __(1)__{title="nastavení parametrů funkce Export Raster"} --> *Extract by Mask* __(2)__{title="nastavení parametrů funkce Extract by Mask"}
        
            **pozn. v případě potřeby exportujte rastr pro své území po více (vzájemně se překrývajících) částech, poté oba rastry spojte nástrojem Mosaic to New Raster*
    2. připrava vektorových vrstev
        -  přes *Add Data From Path* přidejte do mapy požadované vrstvy ze [**ZABAGED_POLOHOPIS**](https://ags.cuzk.gov.cz/arcgis/rest/services/ZABAGED_POLOHOPIS/MapServer "https://ags.cuzk.gov.cz/arcgis/rest/services/ZABAGED_POLOHOPIS/MapServer"){ target="_blank"} z mapových služeb ArcGIS REST
        - z vrstev mapové služby hromadně extrahujte pouze prvky v rozsahu území ORP *(Select-batch)*
        - z vrstvy ``Orná půda a ostatní dále nespecifikované plochy`` vyberte pouze požadované typy ploch *(Select By Attributes)* 
        - vybrané vrstvy hromadně ořízněte dle thranic ORP *(Clip-batch)*
        - jednotlivé vrstvy spojte do jedné vrstvy *(Merge)* 
        - v atributové tabulce nově vzniklé vrstvy vytvořte nový atribut ``hodnoceni`` *(Add Field)*--> hodnoty pro jednotlivé typy ploch vyplňte dle zadaných kritérií *(Calculate Field)*
        - polygonovou vrstvu převeďte na rastr *(Feature to Raster)* __(3)__{title="nastavení parametrů funkce Feature to Raster"} __(4)__{title="nastavení Environments funkce Feature to Raster"}
    3. vytvořte rastry sklonitosti *(Slope)* a orientace svahů *(Aspect)* (nezapomeňte v *Environments* nastavit parametry *Output Coordinate System*, *Cell Size* a *Snap Raster*)
    4. proveďte reklasifikaci rastrů sklonitosti a orientace svahů dle zadaných kritérií *(Reclassify)* __(5)__{title="nastavení parametrů nástroje Reclassify pro rastr orientace svahů"}
    5. zkombinujte rastry využití plochy, sklonitosti a orientace svahů do jednoho rastru, jež bude území ORP klasifikovat dle bodového hodnocení zadaných podmínek *(Raster Calculator)* __(6)__{title="nástroj Raster Calculator"}
    6. výstupní rastr opět reklasifikujte, aby zobrazoval pouze území vhodné pro výstavbu solární elektrárny (minimálně 7 bodů)
    7. převeďte rastr na polygonovou vrstvu *(Raster to Polygon)* a vyberte pouze území splňující zadané kritérium, které je větší než 1 ha *(Select By Attributes)*
    8. polygonovou vrstvu vhodně upravte *(Eliminate Polygon Part)* a vizualizujte *(Symbology)*

<hr class="level-1">

### :material-tower-fire:{ .lg .middle } **ROZHLEDNA**

Z 5 nejvyšších výškových bodů v zadaném ORP identifikujte **nejvhodnější lokalitu pro výstavbu rozhledny**{style="text-transform:uppercase;"}. Hlavním kritériem výběru lokality je viditelnost co největší plochy v okruhu 20 km zadaného ORP. Maximální přípustná výška stavby je 35 m, přičemž pozorovací ochoz je ve výšce 32 m. Zjistěte, jaká je viditelnost významných budov (kostel, zámek, hrad).

Na základě výsledků analýzy vytvořte 3D scénu zobrazující vhodné lokality pro výstavbu rozhledny s modelovanou viditelností. Ve scéně můžete libovolně vyznačit budovy či významné krajinné prvky, které jsou z dané lokality viditelné. Volitelně můžete namodelovat i samotnou stavbu rozhledny.

- **DATOVÉ ZDROJE:**

    [:material-layers: DMP1G ](https://ags.cuzk.gov.cz/arcgis2/rest/services/dmp1g/ImageServer){ .md-button .md-button--primary .button_smaller target="_blank"}
    [:material-layers: Data50 ]("''KotovanyBod', 'Kostel', 'VezovitaStavba', 'Zamek', 'Zricenina', 'Hrad''"){ .md-button .md-button--primary .button_smaller}
    [:material-layers: ZABAGED ]("''KotovanyBod', 'BudovaJednotlivaNeboBlokBudov''"){ .md-button .md-button--primary .button_smaller}
    {: .button_array style="justify-content:flex-start;"}

???+ task-fg-color "Jak na to?"
    1. příprava území pro analýzu
        - kolem území ORP vytvořte obalovou zónu o šířce 20 km *(Buffer)* __(21)__{title="nastavení parametrů nástroje Buffer"}
    2. příprava DMP1G
        - *Add Data From Path* --> *Data-Export Raster* __(22)__{title="nastavení parametrů funkce Export Raster"} --> *Extract by Mask* __(24)__{title="nastavení parametrů funkce Extract by Mask"}
        
            **pozn. v případě potřeby exportujte rastr pro své území po více (vzájemně se překrývajících) částech, poté oba rastry spojte nástrojem Mosaic to New Raster* __(23)__{title="nastavení parametrů funkce Mosaic To New Raster"}       
    3. přidání dat
        - přes *Add Data From Path* přidejte do mapy vrstvu ``KotovanyBod`` z mapových služeb ArcGIS REST ze [**ZABAGED_POLOHOPIS**](https://ags.cuzk.gov.cz/arcgis/rest/services/ZABAGED_POLOHOPIS/MapServer "https://ags.cuzk.gov.cz/arcgis/rest/services/ZABAGED_POLOHOPIS/MapServer"){ target="_blank"} nebo [**DATA50**](https://ags.cuzk.gov.cz/arcgis/rest/services/DATA50/MapServer "https://ags.cuzk.gov.cz/arcgis/rest/services/ZABAGED_POLOHOPIS/MapServer"){ target="_blank"}
        - z vrstvy ``KotovanyBod`` extrahujte pouze prvky v rozsahu území ORP *(Select)* __(25)__{title="nastavení rozsahu zpracování v nástroji Select"}
        - extrahované vrstvy dodatečně hromadně ořízněte dle tvaru území ORP *(Clip)*
        - v atributové tabulce vrstvy vyberte pouze 5 nejvyšších kót ve Vašem ORP a vytvořte novou vrstvu bodových prvků *(Data-Export Features)*
    3. analýza viditelnosti
        - vytvořte rastr viditelnosti pro vrstvu s 5 výškovými kótami *(Visibility)* (nezapomeňte v *Observer parameters* nastavit parametr *Observer offset* dle výšky pozorovatele na plošině rozhledny. Pro větší přesnost výpočtu je vhodné nastavit i parametr *Observer elevation*, který lze převzít z atributové tabulky vrstvy s kótovanými body) __(8)__{title="nastavení parametrů funkce Visibility"}
    4. vyberte lokalitu, ze které je vidět největší plocha Vašeho území
        - pro jednotlivé výškové kóty (OBSXY) postupně sumarizujte počet viditelných pixelů *(název atributu-Summarize)* __(9)__{title="nastavení funkce Summary Statistics"} 
        - dle jednotlivých sumarizačních tabulek určete, která lokalita má pro hodnotu "1" největší počet pixelů __(10)__{title="počet pixelů viditelných z dané lokality"}
    5. vytvořte vizualizaci rastru viditelnosti pro vybranou lokalitu
        - v nastavení symbologie vrstvy nastavte *Primary symbology-Unique Values* dle atributu vybraného lokality (např. OBS1) __(11)__{title="nastavení symbologie rastru viditelnosti"}

<hr class="level-1">

### :material-dump-truck:{ .lg .middle } **SKLÁDKA**

V zadaném ORP identifikujte **vhodné plochy pro výstavbu skládky**{style="text-transform:uppercase;"}.

Při analýze zohledněte následující podmínky:

<div style="text-align:center;" markdown>

| Podmínka | Vzdálenost/hodnota |
|---|---------------------------|
| Záplavové území | mimo Q20 a nižší |
| Vzdálenost od vodního toku nebo plochy | min.	200 m |
| Vzdálenost od OPVZ a OPVN | min. 200 m |
| Vzdálenost od stavebního objektu <br> (`zpusobvyuzitikod = 2,3,4,5,6,7,8,9,10,11,13,14,15`) | min. 300 m |
| Vzdálenost od MZChÚ či OP MZChÚ | min. 300 m |

</div>
Plocha pro výstavbu skládky je považována za vhodnou, pokud má **rozlohu více než 1 ha** a nachází se na **trvalém travním porostu**.

Z výsledků analýzy vyberte **3 nejvhodnější lokality pro výstavbu skládky**{style="text-transform:uppercase;"} dle jejich vzdálenosti od pozemní komunikace a lesa. Ve finálním výběru prioritizujte lokality, které se nachází co nejdále od lesa, ale zároveň nejsou příliš vzdáleny od pozemní komunikace (silnice III. třídy a vyšší).

Vytvořte přehlednou vizualizaci zobrazující vybrané lokality. Ve výsledné vizualizaci uveďte pro jednotlivé lokality následující atributy: plocha v hektarech, vzdálenost od nejbližší silnice a lesa v metrech.


<figure markdown>
  ![Ukázka vizualizace analýzy pro výstavbu skládky v ORP Mělník](../assets/SP/Melnik_skladka_TOP3.png "Ukázka vizualizace analýzy pro výstavbu skládky v ORP Mělník"){ width=600px }
  <figcaption>Ukázka vizualizace analýzy pro výstavbu skládky v ORP Mělník</figcaption>
</figure>


- **DATOVÉ ZDROJE:**

    [:material-layers: RÚIAN ](https://ags.cuzk.gov.cz/arcgis/rest/services/RUIAN/MapServer "''StavebniObjekt', 'ObecSRozsirenouPusobnosti''"){ .md-button .md-button--primary .button_smaller target="_blank"}
    [:material-layers: HEIS VÚV ](https://heis.vuv.cz/data/spusteni/identchk.asp?typ=03 "''Ochranná pásma vodních zdrojů', 'Ochranná pásma vodárenských nádrží', 'Záplavová území Q20''"){ .md-button .md-button--primary .button_smaller target="_blank"}
    [:material-layers: AOPK ](https://data.nature.cz/ "''Maloplošná zvláště chráněná území', 'Ochranná pásma MZCHÚ''"){ .md-button .md-button--primary .button_smaller}
    [:material-layers: ZABAGED ](https://ags.cuzk.gov.cz/arcgis/rest/services/ZABAGED_POLOHOPIS/MapServer "''Lesní půda se stromy', 'Silnice, dálnice', 'Trvalý travní porost', 'Vodní plocha', 'Vodní tok''"){ .md-button .md-button--primary .button_smaller}
    {: .button_array style="justify-content:flex-start;"} 


???+ task-fg-color "Jak na to?"
    
    1. přidání dat
        - přes *Add Data From Path* přidejte do mapy požadované vrstvy od [**RÚIAN**](https://ags.cuzk.gov.cz/arcgis/rest/services/RUIAN/MapServer "https://ags.cuzk.gov.cz/arcgis/rest/services/RUIAN/MapServer"){ target="_blank"} a [**ZABAGED_POLOHOPIS**](https://ags.cuzk.gov.cz/arcgis/rest/services/ZABAGED_POLOHOPIS/MapServer "https://ags.cuzk.gov.cz/arcgis/rest/services/ZABAGED_POLOHOPIS/MapServer"){ target="_blank"} z mapových služeb ArcGIS REST 
        - přes *Catalog-Servers* (či *Insert-Connections*) připojte mapové služby WFS od [**AOPK**](https://gis.nature.cz/arcgis/services/Aplikace/Opendata/MapServer/WFSServer "https://gis.nature.cz/arcgis/services/Aplikace/Opendata/MapServer/WFSServer"){ target="_blank"} a [**HEIS VÚV**](https://ags2.vuv.cz/arcgis/services/isvs_voda/isvs_voda/MapServer/WFSServer "https://ags2.vuv.cz/arcgis/services/isvs_voda/isvs_voda/MapServer/WFSServer"){ target="_blank"} a přidejte do mapy požadované vrstvy __(12)__{title="připojení WFS serveru"}
    2. příprava zadaného území
        - z vrstvy ``ObecSRozsirenouPusobnosti`` vytvořte novou vrstvu, která bude obsahovat pouze hranice zadaného ORP *(Select)* __(13)__{title="výběr prvku v nástroji Select"}
        - kolem území ORP vytvořte obalovou zónu o šířce 300 m *(Buffer)* __(14)__{title="nastavení parametrů nástroje Buffer"}
    3. příprava tematických vrstev
        - z vrstev mapových služeb hromadně extrahujte pouze prvky v rozsahu území ORP včetně obalové zóny 300 m *(Select-batch)* __(15)__{title="práce s proměnnou %Name% v názvu vrstvy"} __(16)__{title="nastavení rozsahu zpracování v nástroji Select"}
        - extrahované vrstvy dodatečně hromadně ořízněte dle tvaru území ORP s obalovou zónou 300m *(Clip-batch)*
        - z vrstvy ``StavebniObjekty`` vyberte pouze požadované typy ploch *(Select By Attributes)*
        - vrstvy ``Maloplošná zvláště chráněná území`` a ``Ochranná pásma MZCHÚ`` spojte do jedné vrstvy *(Merge)* 
    4. příprava omezujících ploch
        - kolem příslušných vrstev vytvořte obalovou zónu o zadané šířce *(Buffer-batch)*
        - nově vzniklé vrstvy s obalovými zónami spojte do jedné vrstvy, která bude vymezovat tzv. omezující plochy *(Merge)*
    5. vlastní analýza
        - od plochy zadaného území (bez obalové zóny) odečtěte vrstvu s omezujícími plochami *(Erase)* __(17)__{title="nastavení parametrů nástroje Erase"}
        - nově vzniklou vrstvu prostorově překryjte s vrstvou ``Trvalý travní porost`` *(Intersect)*
        - z prvků nové vrstvy (vytvořené po prostorovém překrytí) vyberte pouze území větší než 1 ha *(Select By Attributes)*
        - výběr exportujte do samostatné vrstvy *(Data-Export Features)* či vhodně nastavte výraz v *Definition Query*
    6. kritérium vzdálenosti
        - pro finální vrstvu prvků nejprve vypočtěte vzdálenost k pozemním komunikacím *(Near)*, vhodně pojmenujte výstupní atribut, např. ``NEAR_DIST_silnice`` __(18)__{title="nastavení parametrů nástroje Near"}
        - poté identickým způsobem vypočtěte pro finální vrstvu prvků i vzdálenost k lesům *(Near)*, vhodně pojmenujte výstupní atribut, např. ``NEAR_DIST_les``
    7. výběr nejvhodnějších lokalit
        - ve finální vrstvě seřaďte atributy dle vzdálenosti k lesu a ve výběru prioritizujte lokality, které se nachází co nejdále od lesa, ale zároveň nejsou příliš vzdáleny od pozemní komunikace (maximálně do 500 m)
    8. mapový poster
        - vybrané prvky vhodně vizualizujte *(Symbology)* a popište (nový sloupec v AT, např. Lokalita 1–3)
        - finalizujte layout:
                
            a. vhodně nastavte parametry layoutu (formát A3, orientace dle charakteru území)
            
            b. vhodně nastavte transparentnost podkladové mapy
            
            c. rozsah hlavní mapy omezte dle obalové zóny ORP *(Map-Properties-Clip layers)*
            
            d. ve vedlejších mapách zobrazte detail vybraných 3 lokalit (duplikace původní mapy, tvorba záložek, kopie map framů)
            
            e. vhodně nastavte referenční měřítko všech map
            
            f. u každé vedlejší mapy uveďte název lokality, její plochu a vzdálenost od lesa a pozemní komunikace (vložte jako dynamický text, plochu uvádějte v ha --> výpočet přes *Calculate Field*, uvádějte max. na 2 desetinná místa)
        
<!-- původní zadání (B241)

|TYP PODMÍNKY| VZDÁLENOST NEBO HODNOTA                     |
|---|---------------------------|
| Plocha | min. 1 ha |
| Půdy | jíl nebo jiná nepropustná hornina |
| Hladina podzemní vody | území s nízkou hladinou podzemní vody |
| Záplavové území | mimo Q20 a nižší |
| Sklonitost terénu | do 4,5° sklonu  |
| Vzdálenost od vodního toku nebo plochy | min.	200 m |
| Vzdálenost od stavebního objektu <br> (`zpusobvyuzitikod = 2,3,4,5,6,7,8,9,10,11,13,14,15`) | min. 300 m |
| Vzdálenost od MZChÚ | min. 300 m |
| Vzdálenost od ChOPAV | min. 500 m |
| Vzdálenost k pozemním komunikacím | silnice III. tř. a vyšší max. 250 m daleko | -->

</div>

1.  ![](../assets/cviceni7/ExportRasterDialog.png){ .no-filter width=500px} nastavení parametrů funkce Export Raster
2.  ![](../assets/cviceni7/ExtractByMask.png){ .no-filter width=500px} nastavení parametrů funkce Extract by Mask
3.  ![](../assets/cviceni7/FeatureToRaster.png){ .no-filter width=500px} nastavení parametrů funkce Feature to Raster
4.  ![](../assets/cviceni7/FeatureToRaster_Environments.png){ .no-filter width=500px} nastavení Environments funkce Feature to Raster
5.  ![](../assets/cviceni7/Reclassify_Aspect.png){ .no-filter width=500px} nastavení parametrů nástroje Reclassify pro rastr sklonitosti
6.  ![](../assets/cviceni7/RasterCalculator.png){ .no-filter width=500px} nástroj Raster Calculator
7.  ![](../assets/cviceni7/SelectByLocation.png){ .no-filter width=500px} výběr prvků na základě polohy
8.  ![](../assets/SP/Visibility.png){ .no-filter width=500px} nastavení parametrů funkce Visibility
9.  ![](../assets/cviceni7/SummaryStat.png){ .no-filter width=500px} nastavení funkce Summary Statistics
10. ![](../assets/cviceni7/SummaryStatTable.png){ .no-filter width=500px} počet pixelů viditelných z dané lokality
11. ![](../assets/cviceni7/Symbology.png){ .no-filter width=500px} nastavení symbologie rastru viditelnosti
12. ![](../assets/SP/WFS.png){ .no-filter width=500px} připojení WFS serveru
13. ![](../assets/SP/Select_VyberORP.png){ .no-filter width=500px} výběr prvku v nástroji Select
14. ![](../assets/SP/buffer.png){ .no-filter width=500px} nastavení parametrů nástroje Buffer
15. ![](../assets/SP/SelectBatch.png){ .no-filter width=500px} práce s proměnnou %Name% v názvu vrstvy
16. ![](../assets/SP/Select_ProcessingExtent_buffer.png){ .no-filter width=500px} nastavení rozsahu zpracování v nástroji Select
17. ![](../assets/SP/erase.png){ .no-filter width=500px} nastavení parametrů nástroje Erase
18. ![](../assets/SP/near.png){ .no-filter width=500px} nastavení parametrů nástroje Near
19. ![](../assets/cviceni7/ExportRasterDialog.png){ .no-filter width=500px} nastavení parametrů funkce Export Raster
20. ![](../assets/cviceni7/ExtractByMask.png){ .no-filter width=500px} nastavení parametrů funkce Extract by Mask
21. ![](../assets/SP/buffer20km.png){ .no-filter width=500px} nastavení parametrů nástroje Buffer
22. ![](../assets/SP/ExportRasterDialog_DMP.png){ .no-filter width=500px} nastavení parametrů funkce Export Raster
23. ![](../assets/SP/MosaicToNewRaster.png){ .no-filter width=500px} nastavení parametrů funkce Mosaic To New Raster
24. ![](../assets/SP/ExtractByMask_DMP.png){ .no-filter width=500px} nastavení parametrů funkce Extract by Mask
25. ![](../assets/SP/Select_ProcessingExtent_buffer.png){ .no-filter width=500px} nastavení rozsahu zpracování v nástroji Select

<hr class="level-1">

## Výstup

???+ note-grey "Forma a obsah semestrální práce"
    Výstup lze odevzdat jako:

    a. **tištěný mapový poster** o velikosti min. **A2**, který bude obsahovat základní charakteristiku území ORP (rozloha, počet obyvatel a slovní popis území), zadání jednotlivých analýz a zejména mapové vizualizace výstupů všech analýz (včetně pohledu 3D scény*), které budou doprovozeny textem interpretujícím výsledky (např. kolik % plochy ORP je vhodných pro výstavbu daného objektu, které lokality a proč byly vybrány jako nejvhodnější). 
    
    b. **tištěný dokument**, který bude obsahovat textovou část a obrazové přílohy. V textové části bude uvedena základní charakteristika území ORP (rozloha, počet obyvatel a slovní popis území), zadání jednotlivých analýz a text interpretující výsledky (např. kolik % plochy ORP je vhodných pro výstavbu daného objektu, které lokality a proč byly vybrány jako nejvhodnější). Obrazové přílohy pak budou tvořit mapové vizualizace výstupů všech analýz (včetně pohledu 3D scény*).
    
    c. **webovou mapovou aplikaci/story mapu**, která bude obsahovat základní charakteristiku území ORP (rozloha, počet obyvatel a slovní popis území), zadání jednotlivých analýz a zejména vizualizace výstupů všech analýz ve formě webových map (včetně pohledu 3D scény*), které budou doprovozeny textem interpretujícím výsledky (např. kolik % plochy ORP je vhodných pro výstavbu daného objektu, které lokality a proč byly vybrány jako nejvhodnější).

    **3D scénu lze vytvořit ve webovém prostředí a v tištěném výstupu na ní pouze vhodně odkázat (link, QR kód)*


Termín odevzdání: __čtvrtek 29. ledna 2026__{.outlined} 


<!--

Nad zadaným územím proveďte následující analýzy s využitím GIS softwaru. Výsledky jednotlivých úloh následně publikujte formou webové mapové aplikace na ArcGIS Online či pomocí open-source řešení (např. GISQuick). Tato aplikace může mít libovolnou formu, takovou, kterou uznáte za vhodnou či zajímavou (ArcGIS Instant Apps, Story Maps, Experience Builder,...). 

Svou aplikaci na konci semestru **30.4.2024** krátce odprezentujete před ostatními v 5 minutové prezentaci. 

Dotazy či připomínky k semestrální práci směřujte sem: *frantisek.muzik@fsv.cvut.cz*

**Pro zadané území vypracujte následující úkoly:**

**1.** Zjistěte v jaké obci se nachází zadaný definiční bod. Z databáze RÚIAN tuto obec vyberte a vyexportujte ji do samostatné vrstvy.

**2.** Určete počet adresních míst na území dané obce (zdroj: RÚIAN).

**3.** Zjistěte, zda se na území zadané obce a v 10 km kolem ní nachází chráněné území (zdroj: ZABAGED). Pokud ano, zobrazte jej v mapě jako samostatnou vrstvu. 

**4.** Vytvořte samostatnou vrstvu, která bude obsahovat data způsobu využití pozemku (zdroj: RÚIAN – vrstva *Parcela*). Na základě atributů v tabulce níže vypočítejte pro data nový sloupec *TYP_VYUZITI*, na základě kterého vrstvu následně vhodně vizualizujte. Číselníky pro přiřazení kódů: [Způsob využití pozemku](https://www.cuzk.cz/Katastr-nemovitosti/Poskytovani-udaju-z-KN/Ciselniky-ISKN/Ciselniky-k-nemovitosti/Zpusob-vyuziti-pozemku.aspx), [Kód druhu pozemku](https://www.cuzk.cz/Katastr-nemovitosti/Poskytovani-udaju-z-KN/Ciselniky-ISKN/Ciselniky-k-nemovitosti/Druh-pozemku.aspx). Závěrem proveďte *Dissolve* dle atributu *TYP_VYUZITI*.

|  Typ využití pozemku *TYP_VYUZITI* (vypočtené)       | Kód druhu pozemku *SC_D_POZEMKU*        | Způsob využití pozemku *SC_ZP_VYUZITI_POZ*            
| ------------ | ------------------------- |----------------|
| orná půda    | 2 | -|
| lesní půda | 10 |  -|
| trvalý travní porost   | 7, 8 | -|
| zahrada    | 5, 6 | -|
| vodstvo   | 11 | -|
| zastavěná plocha     |  13  | *Null* |
| nádvoří     |  13  | *Not Null* |
| komunikace   | 3, 4 , 14 | 14, 15, 16, 17|
| ostatní   | 3, 4 , 14 | vše kromě 14, 15, 16, 17|


???+ note "&nbsp;<span style="color:#448aff">Poznámka</span>"
      V případě určování typu využití pozemku (sloupec *TYP_VYUZITI*) pro atributy *ostatní* a *komunikace* musí platit výběr prvků ze sloupců *Kód druhu pozemku* a *Způsob využití pozemku* zároveň (tedy využití *AND* ve funkci *Select by attributes*).

**5.** Georeferencujte rastry Státní mapy 1 : 5 000 – odvozené (SMO5) z 50. let 20. století. Najdete je na disku S. Georeferencujte pouze rastry, kterých se dotýká území v okruhu 500 metrů od definičního bodu obce. Ten vypočítejte jako těžiště polygonu obce (musí být uvnitř polygonu). Z georeferencovaných rastrů vytvořte mozaiku. Rastrovou mapu SMO5 neexportujte do výsledné webové aplikace.

**6.** Na podkladu SMO5 vektorizujte území v okruhu 500 metrů od definičního bodu obce. Tato data slučte na základě typů využití ploch (funkce Dissolve). 

Rozlišujte následující typy využití ploch (stejně jako v bodě 5 pro data z RÚIAN): 

- orná půda

- lesní půda

- trvalý travní porosty (louky, pastviny)

- zahrada

- vodstvo (řeky, potoky, rybníky), nevektorizujte malé vodní toky vyznačené pouze liniově

- zastavěná plocha

- nádvoří (okolí domů, neoznačené zahrady, veřejné prostory v intravilánu)

- komunikace (cesty, silnice, železnice)

- ostatní lomy, neúrodná půda apod.

<figure markdown>
![SMO5_legenda](../assets/cviceni6/SMO5_legenda.png "Legenda SMO5"){ width="600" }
    <figcaption>Značkový klíč SMO5</figcaption>
</figure>

**7.** Vektorizaci SMO5 topologicky zkontrolujte dle pravidel *Must Not Have Gaps (Area)*, *Must Not Overlap With (Area-Area)* a *Must Not Overlap (Area)*.

**8.** Ve výsledné aplikaci porovnejte vývoj využití krajiny v 50. letech 20. století (vektorizace z SMO5) se současností (RÚIAN – vrstva *Parcela*). Způsob porovnání zvolte dle vlastního uvážení (posuvník v aplikaci, nová vrstva s vypočtenými rozdíly apod.).

**9.** Jako samostatnou vrstvu do svého projektu připojte WMS, WMTS či WFS službu dle vašeho výběru (např. historickou mapu, ortofoto či katastrální mapu). Tato vrstva musí být součástí výsledné mapové aplikace.

## Konkrétní zadání
Bude rozesláno emailem.

-->

