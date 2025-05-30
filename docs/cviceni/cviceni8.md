---
icon: material/numeric-8-box
title: Cvičení 8
---

# 3D vizualizace v GIS

<div class="gallery_container" markdown>
![](../assets/cviceni8/img_01_edit.jpg){: .no-filter }
![](../assets/cviceni8/img_02_edit.jpg){: .no-filter }
![](../assets/cviceni8/img_03_edit.jpg){: .no-filter }
![](../assets/cviceni8/img_04_edit.jpg){: .no-filter }
![](../assets/cviceni8/img_05_edit.jpg){: .no-filter }
![](../assets/cviceni8/img_06_edit.jpg){: .no-filter }
![](../assets/cviceni8/img_07_edit.jpg){: .no-filter }
![](../assets/cviceni8/img_08_edit.jpg){: .no-filter }
</div>

<style>
    .smaller_padding li {padding:.4rem .8rem !important;}
    .primary_color {color:var(--md-primary-fg-color);}
</style>


<!-- <hr class="level-1"> -->

## Náplň cvičení
Úkolem je **vytvořit 3D scénu** (v ArcGIS Pro a ArcGIS Online) na podkladech dostupných GIS dat.  
**Scéna bude obsahovat**:


<div style="margin-left:1rem;" markdown>
:material-terrain:{.lg .middle style="margin-right:.4em"} rastrový model terénu

:fontawesome-solid-house:{.lg .middle style="margin-right:.4em"} zjednodušené 3D modely budov (s výškami odvozenými z hodnot atributu)

:material-tree:{.lg .middle style="margin-right:.4em"} 3D modely vegetace (stromů, rozlišení min. dvou druhů)

:fontawesome-solid-building-columns:{.lg .middle style="margin-right:.4em"} 3D model významného objektu (rozhledny)
</div>

![](../assets/cviceni8/img_102.gif){: .no-filter width="600em"}
{align=center}

<hr class="level-1">

## Pracovní postup

**Model terénu**

- výřez rastru z webové služby [Geoportálu ČÚZK](https://geoportal.cuzk.cz/(S(grqmhsoejjqzgx4ofarvzeq0))/Default.aspx?mode=TextMeta&text=uvod_uvod&head_tab=sekce-00-gp&menu=01&news=yes "→ Služby → Prohlížecí → Služby Esri ArcGIS Server → IMAGE služba AGS - Digitální model reliéfu České republiky 5. generace (DMR 5G)"){.underlined_dotted} – nástroj **:material-briefcase: Clip Raster**{.no-dec .outlined} nebo **:material-briefcase: Copy Raster**{.no-dec .outlined}

![](../assets/cviceni8/img_201.png)
![](../assets/cviceni8/img_202.png)
![](../assets/cviceni8/img_203.png)
{.process_container}

- nastavení rastru jako "*Ground*" v lokální scéně ArcGIS Pro

![](../assets/cviceni8/img_204.png)
![](../assets/cviceni8/img_205.png)
{.process_container}

**Zjednodušené modely budov**

- extrakce prvků z webové služby [Geoportálu ČÚZK](https://geoportal.cuzk.cz/(S(grqmhsoejjqzgx4ofarvzeq0))/Default.aspx?mode=TextMeta&text=uvod_uvod&head_tab=sekce-00-gp&menu=01&news=yes "→ Služby → Prohlížecí → Služby Esri ArcGIS Server → Mapová služba nad daty RÚIAN → podvrstva StavebniObjekt (3)"){.underlined_dotted} – nástroj **:material-briefcase: Select**{.no-dec .outlined} (s nastaveným výběrem či rozsahem zobrazení)

![](../assets/cviceni8/img_301.svg){width=300}
{align=center}

- funkce extrusion (max height), expression: `Ceil(Random()*10+15)` nebo `pocet_podlazi*4` – vytáhne polygon podél osy Z o náhodný počet metrů v rozmezí 16 až 25 metrů nebo o počet podlaží ×4 metry

![](../assets/cviceni8/img_303.jpg){width=300}
{align=center}

- volitelně přidat atribut "barva" s náhodnými hodnotami od 1 do 4 (barva fasády)
- konverze geometrie z Polygon do Multipatch – nástroj **:material-briefcase: Layer 3D to Feature Class**{.no-dec .outlined} (nástroj zapíše do databáze extrudované polygony jako 3D geometrii)

![](../assets/cviceni8/img_311.png)
{.process_container}

**Vegetace**

- získání ploch s vegetací ve formě polygonů (extrakce prvků z webové vrstvy ZABAGED či ručním kreslením)

![](../assets/cviceni8/img_302.svg){width=300}
{align=center}

- rozmístění bodů s náhodnou polohou v ploše polygonů – nástroj `Create Spatial Sampling Locations`

![](../assets/cviceni8/img_304.png)
{.process_container}

- přidání číselného atributu "druh" rozlišujícího dva druhy stromu, které budou v 3D scéně rozlišeny odlišnými 3D modely
- vyplnění atributu "druh" náhodnými hodnotami 1 a 2 – nástroj `Calculate Field`, expression: `Ceil(Random()*2)`
- *volitelně: přidání číselného atributu "rotace" a jeho vyplnění náhodnými hodnotami azimutu (0 až 360°), tento atribut bude reprezentovat otočení modelu stromu, čímž scéně dodá na realističnosti

![](../assets/cviceni8/img_305.png)
{.process_container}

- nastavení 3D bodové symboliky

![](../assets/cviceni8/img_306.png)
![](../assets/cviceni8/img_307.png)
![](../assets/cviceni8/img_309.png)
![](../assets/cviceni8/img_310.png)
![](../assets/cviceni8/img_308.jpg)
{.process_container}

- ~~konverze geometrie z Point do Multipatch – nástroj **:material-briefcase: Layer 3D to Feature Class**{.no-dec .outlined} (nástroj zapíše do databáze bodovou 3D symboliku jako 3D geometrii)~~

**3D model významného objektu**

- získání souboru s modelem (formáty .DAE, .DWG, .FBX, .GLB, .GLTF, .IFC, .OBJ, .USDC, .USDZ, event. .IFC), příkladový model (Petřínská rozhledna) zde: [:material-cube-outline: OBJ](../assets/cviceni8/petrinska_rozhledna.obj){.md-button .md-button--primary .button_smaller}, [:material-cube-outline: MTL](../assets/cviceni8/petrinska_rozhledna.mtl){.md-button .md-button--primary .button_smaller}
- import modelu do geodatabáze – nástroj `Import 3D Files` ~~nebo `Import 3D Objects`~~ (nastavit souřadnicový systém na S-JTSK 5514, ~~pozor na orientaci modelu – "Y is up"~~)
- ~~posun modelu na správné souřadnice – editační nástroj `Move to`~~

![](../assets/cviceni8/img_312.jpg){width=300}
{align=center}

---

**Export do webové scény**

- Budovy a rozhledna: konverze do formátu SLPK (balíček optimalizovaný pro zobrazení na webu) – nástroj `Create 3D Object Scene Layer Content` (nastavit souřadnicový systém na Web Mercator 3857 a správnou transformaci)

![](../assets/cviceni8/img_313.png)
{.process_container}

- Stromy: je možné aplikovat stjený postup (konverze do formátu SLPK, 3D symbolika zvolená v ArcGIS Pro bude pevně zapsána jako 3D geometrie) NEBO je možné data publikovat jako bodovou vrstvu (bez konverze, symboliku bude možné zvolit ve webové scéně jako 3D bodový symbol)

- publikace do ArcGIS Online

![](../assets/cviceni8/img_316.png)
![](../assets/cviceni8/img_314.png)
![](../assets/cviceni8/img_315.png)
{.process_container}

- konfigurace a sdílení scény

**Datové zdroje**

[<span>geoportal.cuzk.cz</span><br>DMR 5G](https://geoportal.cuzk.cz/(S(grqmhsoejjqzgx4ofarvzeq0))/Default.aspx?mode=TextMeta&side=wms.AGS&text=WMS.AGS&head_tab=sekce-03-gp&menu=314){ .md-button .md-button--primary .server_name .external_link_icon_small target="_blank"}
[<span>geoportal.cuzk.cz</span><br>RÚIAN](https://geoportal.cuzk.cz/(S(grqmhsoejjqzgx4ofarvzeq0))/Default.aspx?mode=TextMeta&side=wms.AGS&text=WMS.AGS&head_tab=sekce-03-gp&menu=314){ .md-button .md-button--primary .server_name .external_link_icon_small target="_blank"}
[<span>geoportal.cuzk.cz</span><br>ZABAGED](https://geoportal.cuzk.cz/(S(grqmhsoejjqzgx4ofarvzeq0))/Default.aspx?mode=TextMeta&side=wms.AGS&text=WMS.AGS&head_tab=sekce-03-gp&menu=314){ .md-button .md-button--primary .server_name .external_link_icon_small target="_blank"}
[<span>&nbsp;</span><br>3D model význ. objektu](../assets/cviceni8/petrinska_rozhledna.obj){ .md-button .md-button--primary .server_name .external_link_icon_small target="_blank"}
{.button_array}

---

**Schéma pracovního postupu**

``` mermaid
graph TD
  A[("`**model terénu**
  rastr [2m/px]
  DMR 5G (ČÚZK)`")]
  B[("`**půdorysy budov**
  polygonová třída prvků
  RÚIAN (ČÚZK)`")]
  C[("`**lesní plochy**
  polygonová třída prvků
  ZABAGED (ČÚZK)`")]
  D[("`**podrobný 3D model budovy**
  formát OBJ, FBX, DWG aj.
  vlastní zdroj`")]

  E([Clip Raster])
  F([Select])
  G([Select])
  H([Import 3D Files])

  I(["`Create Spatial
  Sampling Locations`"])
  J([Create 3D Object Scene Layer Content])

  L[rastr jako Ground Elev. Surface]
  M["`extruze<br>pocet_pater*4`"]
  N["`bodová 3D symbolika<br>(stromy)`"]
  O(["`Calculate Field<br>přidat atribut 'druh'`"])
  P(["`Calculate Field<br>přidat atribut 'barva'`"])

  Q[publikace do ArcGIS Online]
  R[konfigurace webové scény]

  A-->E
  B-->F
  C-->G
  D-->H

  G-->I
  H-->J

  E---->L
  F--->P
  I-->O
  O-->N
  P-->M

  J---->Q
  N-->Q
  M-->Q

  Q-->R

  click I "https://pro.arcgis.com/en/pro-app/latest/tool-reference/data-management/create-spatial-sampling-locations.htm"
  click J "https://pro.arcgis.com/en/pro-app/latest/tool-reference/data-management/create-3d-object-scene-layer-package.htm"
  click E "https://pro.arcgis.com/en/pro-app/latest/tool-reference/data-management/clip.htm"
  click F "https://pro.arcgis.com/en/pro-app/latest/tool-reference/analysis/select.htm"
  click G "https://pro.arcgis.com/en/pro-app/latest/tool-reference/analysis/select.htm"
  click H "https://pro.arcgis.com/en/pro-app/latest/tool-reference/3d-analyst/import-3d-files.htm"

  classDef default fill:#00948522,stroke:#009485,stroke-width:3px;

```




