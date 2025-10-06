---
icon: material/numeric-2-box
title: Souřadnicové ref. systémy, připojení negisovských dat
---

# Souřadnicové referenční systémy v ČR | přehled typů dat a zdrojů, webové mapové služby | připojení externích dat

## Cíl cvičení

Seznámení se s definicí souřadnicových referenčních systémů v GIS. Proběhne představení zdrojů gisovských i negisovských dat, použitelných pro analýzy a vizualizace, včetně webových mapových služeb a cloudových služeb ArcGIS Online. Naučíme se připojit externí (negisovská) data, např. tabulky XLS, CSV textové soubory aj.


# Práce s externími daty (Excel, CSV), join

Na rozdíl od předchozích úloh, kdy byla práce zaměřena na práci s poskytnutými prostorovými daty uloženými v geodatabázi či formátu SHP, se následující úloha soustředí na možnosti importu externích tabelárních dat a jejich připojení na prostorová data.

Prostřednictvím společného pole (klíče) lze přiřadit záznamy v jedné tabulce se záznamy v jiné tabulce (vrstvě). K vrstvě parcel můžete například přidružit tabulku informací o vlastnictví parcel, protože sdílejí pole identifikace parcely. Tato přidružení můžete vytvořit několika způsoby, včetně dočasného spojení či vytvoření trvalejších tříd vztahů uvnitř geodatabáze. Spojení může být také založeno na prostorovém umístění, jak bude demonstrováno v dalším cvičení č. 4.

## Základní pojmy

[<span>:material-open-in-new: pro.arcgis.com</span><br>Join the attributes from a table](https://pro.arcgis.com/en/pro-app/latest/help/data/tables/joins-and-relates.htm#GUID-39C9610A-6A73-4985-ADB8-7354EA9DB8BF){ .md-button .md-button--primary .url-name target="_blank"}
[<span>:material-open-in-new: pro.arcgis.com</span><br>Join data by location (spatially)](https://pro.arcgis.com/en/pro-app/latest/help/data/tables/joins-and-relates.htm#GUID-7B11EAA4-35E0-4B8D-AFB6-4A435761574B){ .md-button .md-button--primary .url-name target="_blank"}
[<span>:material-open-in-new: pro.arcgis.com</span><br>Remove join](https://pro.arcgis.com/en/pro-app/latest/help/data/tables/joins-and-relates.htm#ESRI_SECTION1_6507320BCB1E45219A88F1AA0A24F7B9){ .md-button .md-button--primary .url-name target="_blank"}
{: align=center style="display:flex; justify-content:center; align-items:center; column-gap:20px; row-gap:10px; flex-wrap:wrap;"}

