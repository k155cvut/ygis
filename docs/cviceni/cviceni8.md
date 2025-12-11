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

### Model terénu

- výřez rastru z webové služby [Geoportálu ČÚZK](https://geoportal.cuzk.cz/(S(grqmhsoejjqzgx4ofarvzeq0))/Default.aspx?mode=TextMeta&text=uvod_uvod&head_tab=sekce-00-gp&menu=01&news=yes "→ Služby → Prohlížecí → Služby Esri ArcGIS Server → IMAGE služba AGS - Digitální model reliéfu České republiky 5. generace (DMR 5G)"){.underlined_dotted}: služba [**IMAGE služba AGS - (DMR 5G)**](https://ags.cuzk.gov.cz/arcgis2/rest/services/dmr5g/ImageServer) – nástroj **:material-briefcase: Export Raster**{.no-dec .outlined}

![](../assets/cviceni8/img_321.png)
![](../assets/cviceni8/img_322.png)
![](../assets/cviceni8/img_323.png)
{.process_container}

- nastavení rastru jako "*Ground*" v lokální scéně ArcGIS Pro

![](../assets/cviceni8/img_204.png)
![](../assets/cviceni8/img_205.png)
{.process_container}

---




### Zjednodušené modely budov

- extrakce prvků z webové služby [Geoportálu ČÚZK](https://geoportal.cuzk.cz/(S(grqmhsoejjqzgx4ofarvzeq0))/Default.aspx?mode=TextMeta&text=uvod_uvod&head_tab=sekce-00-gp&menu=01&news=yes "→ Služby → Prohlížecí → Služby Esri ArcGIS Server → Mapová služba nad daty RÚIAN → podvrstva StavebniObjekt (3)"){.underlined_dotted} – nástroj **:material-briefcase: Select**{.no-dec .outlined} (s nastaveným výběrem či rozsahem zobrazení)

![](../assets/cviceni8/img_301.svg){width=300}
{align=center}

- zapsání výšek do polygonů s půdorysy stavebních objektů (konverze z typu XY do typu XY**Z**)

![](../assets/cviceni8/img_324.png){width=300}
{.process_container}

- funkce extrusion (max height), expression: `Ceil(Random()*10+15)` nebo `pocet_podlazi*4` – vytáhne polygon podél osy Z o náhodný počet metrů v rozmezí 16 až 25 metrů nebo o počet podlaží ×4 metry

![](../assets/cviceni8/img_303.jpg){width=300}
{align=center}

- volitelně přidat atribut "barva" s náhodnými hodnotami od 1 do 4 (barva fasády)
- konverze geometrie z Polygon do Multipatch – nástroj **:material-briefcase: Layer 3D to Feature Class**{.no-dec .outlined} (nástroj zapíše do databáze extrudované polygony jako 3D geometrii)

![](../assets/cviceni8/img_311.png)
{.process_container}

---




### Vegetace

- získání ploch s vegetací ve formě polygonů (extrakce prvků z webové vrstvy ZABAGED – Polohopis či ručním kreslením)
- ve městě fungují dobře vrstvy "Okrasná zahrada, park (134)" nebo "Ovocný sad, zahrada (135)", mimo města pak např. "Lesní půda se stromy (142)"

![](../assets/cviceni8/img_302.svg){width=300}
{align=center}

- rozmístění bodů s náhodnou polohou v ploše polygonů – nástroj `Create Spatial Sampling Locations`
- parametry "Number of Samples" a "Min. Dist. Between Sample Points" odhadněte na základě hustoty výsledku (hodnotu nepřehánět, webová scéna je potom pomalá)

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

- nastavení 3D bodové symboliky je pouze pro ArcGIS Pro (pro případné rendery nebo animace) – při exportu na web budeme exportovat pouze body jako takové, ArcGIS Online má modely vegetace vlastní

- ~~konverze geometrie z Point do Multipatch – nástroj **:material-briefcase: Layer 3D to Feature Class**{.no-dec .outlined} (nástroj zapíše do databáze bodovou 3D symboliku jako 3D geometrii)~~

---




### 3D model významného objektu

- získání souboru s modelem (formáty .DAE, .DWG, .FBX, .GLB, .GLTF, .IFC, .OBJ, .USDC, .USDZ, event. .IFC), příkladový model (Petřínská rozhledna) zde: [:material-cube-outline: OBJ](../assets/cviceni8/petrinska_rozhledna.obj){.md-button .md-button--primary .button_smaller}, [:material-cube-outline: MTL](../assets/cviceni8/petrinska_rozhledna.mtl){.md-button .md-button--primary .button_smaller}
- import modelu do geodatabáze – nástroj `Import 3D Files` ~~nebo `Import 3D Objects`~~ (nastavit souřadnicový systém na S-JTSK 5514, ~~pozor na orientaci modelu – "Y is up"~~)
- posun modelu na správné souřadnice – editační nástroj `Move to` (zjištění souřadnic finálního místa přes pravé tl. --> Copy Coordinates --> upravit formát, smazat mezery a písmena)

![](../assets/cviceni8/img_312.jpg){width=300}
{align=center}

---




### Export do webové scény

- Budovy a rozhledna: konverze do formátu SLPK (balíček optimalizovaný pro zobrazení na webu) – nástroj `Create 3D Object Scene Layer Content` (nastavit souřadnicový systém na Web Mercator 3857 a správnou transformaci)

![](../assets/cviceni8/img_313.png)
{.process_container}

- ~~Stromy: je možné aplikovat stejný postup (konverze do formátu SLPK, 3D symbolika zvolená v ArcGIS Pro bude pevně zapsána jako 3D geometrie) NEBO je možné data publikovat jako bodovou vrstvu (bez konverze, symboliku bude možné zvolit ve webové scéně jako 3D bodový symbol)~~

- publikace do ArcGIS Online (proveďte celkem 3×: 1-SLPK vrstva s rozhlednou, 2-SLPK vrstva se stavebními objekty a 3-bodová vrstva se stromy)

![](../assets/cviceni8/img_316.png)
![](../assets/cviceni8/img_314.png)
![](../assets/cviceni8/img_315.png)
{.process_container}

- konfigurace a sdílení scény

---




### Datové zdroje

[<span>geoportal.cuzk.cz</span><br>DMR 5G](https://geoportal.cuzk.cz/(S(grqmhsoejjqzgx4ofarvzeq0))/Default.aspx?mode=TextMeta&side=wms.AGS&text=WMS.AGS&head_tab=sekce-03-gp&menu=314){ .md-button .md-button--primary .server_name .external_link_icon_small target="_blank"}
[<span>geoportal.cuzk.cz</span><br>RÚIAN](https://geoportal.cuzk.cz/(S(grqmhsoejjqzgx4ofarvzeq0))/Default.aspx?mode=TextMeta&side=wms.AGS&text=WMS.AGS&head_tab=sekce-03-gp&menu=314){ .md-button .md-button--primary .server_name .external_link_icon_small target="_blank"}
[<span>geoportal.cuzk.cz</span><br>ZABAGED](https://geoportal.cuzk.cz/(S(grqmhsoejjqzgx4ofarvzeq0))/Default.aspx?mode=TextMeta&side=wms.AGS&text=WMS.AGS&head_tab=sekce-03-gp&menu=314){ .md-button .md-button--primary .server_name .external_link_icon_small target="_blank"}
[<span>&nbsp;</span><br>3D model význ. objektu](../assets/cviceni8/petrinska_rozhledna.obj){ .md-button .md-button--primary .server_name .external_link_icon_small target="_blank"}
{.button_array}

---




### Schéma pracovního postupu

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

  E([Export Raster])
  F([Select])
  G([Select])
  H([Import 3D Files])

  I([Interpolate Shape])
  J(["`Create Spatial Sampling Locations`"])
  K(["Move To (Editing)"])

  L(["`Calculate Field<br>přidat atribut 'barva'`"])
  M(["`Calculate Field<br>přidat atribut 'druh'`"])

  N[rastr jako Ground Elevation Surface]
  O["`extruze<br>*pocet_pater×4* (nebo jinak)`"]
  P["`bodová 3D symbolika<br>(stromy)`"]

  Q([Layer 3D To Feature Class])

  R([Create 3D Object Scene Layer Content])
  S([Create 3D Object Scene Layer Content])
  T([Create 3D Object Scene Layer Content])

  U["*není nutné publikovat, web. službu už poskytuje přímo ČÚZK*"]
  V[publikace do ArcGIS Online]

  W[nová webová scéna]

  X([přidat vrstvy])

  Y[DMR5G]
  Z[budovy]
  AA[podrobný 3D model budovy]
  AB[stromy]

  AC(["nastavit symboliku podle atributu viditelnosti (a vhodnou barevnou stupnici)"])
  AD(["nastavit 3D symbol (případně náhodné natočení)"])

  AE([uložit scénu])
  AF([nastavit veřejné sdílení])

  
  A-->E
  B-->F
  C-->G
  D-->H

  E---->N
  E-->I
  F-->I
  G-->J
  H--->K

  I-->L
  J-->M
  K---->T
  
  L-->O
  M-->P

  N---->U
  
  O-->Q
  P--->S

  Q-->R

  R-->V
  S-->V
  T-->V

  V-->W

  W-->X

  X-->Y
  X-->Z
  X-->AA
  X-->AB

  Z-->AC
  AB-->AD

  Y--->AE
  AC-->AE
  AA--->AE
  AD-->AE

  AE-->AF

  click E "https://pro.arcgis.com/en/pro-app/latest/help/data/imagery/export-or-convert-raster-datasets.htm" _blank
  click F "https://pro.arcgis.com/en/pro-app/latest/tool-reference/analysis/select.htm" _blank
  click G "https://pro.arcgis.com/en/pro-app/latest/tool-reference/analysis/select.htm" _blank
  click H "https://pro.arcgis.com/en/pro-app/latest/tool-reference/3d-analyst/import-3d-files.htm" _blank
  click I "https://pro.arcgis.com/en/pro-app/latest/tool-reference/3d-analyst/interpolate-shape.htm" _blank
  click J "https://pro.arcgis.com/en/pro-app/latest/tool-reference/data-management/create-spatial-sampling-locations.htm" _blank
  click K "https://pro.arcgis.com/en/pro-app/latest/help/editing/move-a-feature-to-specified-location.htm" _blank
  click L "https://pro.arcgis.com/en/pro-app/latest/tool-reference/data-management/calculate-field.htm" _blank
  click M "https://pro.arcgis.com/en/pro-app/latest/tool-reference/data-management/calculate-field.htm" _blank
  click Q "https://pro.arcgis.com/en/pro-app/latest/tool-reference/3d-analyst/layer-3d-to-feature-class.htm" _blank
  click R "https://pro.arcgis.com/en/pro-app/latest/tool-reference/data-management/create-3d-object-scene-layer-package.htm" _blank
  click S "https://pro.arcgis.com/en/pro-app/latest/tool-reference/data-management/create-3d-object-scene-layer-package.htm" _blank
  click T "https://pro.arcgis.com/en/pro-app/latest/tool-reference/data-management/create-3d-object-scene-layer-package.htm" _blank
  click W "https://doc.arcgis.com/en/arcgis-online/get-started/get-started-with-scenes.htm" _blank

  classDef default fill:#00948522,stroke:#009485,stroke-width:3px;


```

