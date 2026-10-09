## Import CAD dat a jejich prostorové umístění

V projektové dokumentaci se často setkáme s výkresy ve formátu **DXF** nebo **DWG**. ArcGIS Pro umožňuje CAD data přímo načíst a zobrazit spolu s dalšími geografickými daty. Aby však bylo možné výkres správně umístit do mapy, je potřeba vědět, **v jakých souřadnicích byl vytvořen** a zda má **definovaný souřadnicový referenční systém (CRS)**.

V tomto cvičení si vyzkoušíme dva různé případy:

- :material-map-marker-check: **Výkres se skutečnými souřadnicemi, ale bez definovaného CRS** – souřadnice jsou správné, stačí jim přiřadit odpovídající referenční systém.
- :material-crosshairs-gps: **Výkres v lokálních souřadnicích** – kromě přiřazení CRS je nutné výkres také **georeferencovat**, tedy prostorově posunout a případně otočit či změnit jeho měřítko.


### CAD data v ArcGIS Pro

DXF může obsahovat body, linie, polygony, popisy i další prvky organizované do CAD hladin (*layers*). V ArcGIS Pro se CAD soubor zobrazuje jako sada geografických vrstev podle typu geometrie, například **Point**, **Polyline**, **Polygon** a **Annotation**. CAD data jsou při přímém načtení určena především ke čtení; pro další úpravy je lze převést na prvkové třídy geodatabáze.

!!! warning "CAD data a souřadnicové systémy"
    - **Define Projection** určuje, jaký souřadnicový systém mají již uložené souřadnice. **Nemění jejich číselné hodnoty.**
    - **Project** převádí souřadnice mezi dvěma známými souřadnicovými systémy a vytváří nová data.
    - **Georeference** prostorově umisťuje data, jejichž souřadnice neodpovídají skutečné poloze. U CAD dat může zahrnovat posun, otočení a změnu měřítka.

### Úloha A: DXF se skutečnými souřadnicemi, ale bez definovaného CRS

**Vstupní data:** DXF výkres území označeného kódem **614131**. Souřadnice výkresu již odpovídají reálné poloze, ale soubor nemá definovaný souřadnicový referenční systém.

**Cíl:** Správně určit a přiřadit CRS tak, aby se CAD data zobrazila na správném místě bez změny geometrie.

**Postup:**

1. Otevřete ArcGIS Pro a vytvořte nový projekt. Nastavte souřadnicový systém mapy přes *:material-tab: Map Properties*{: .outlined_code} → *:material-form-dropdown: Coordinate Systems*{: .outlined_code}. Pro referenční data v S-JTSK použijte **S-JTSK / Krovak East North (EPSG:5514)**.
2. Přidejte referenční mapu (např. polygony stavebních objektů z RÚIAN nebo vhodnou mapovou službu) a následně načtěte vstupní DXF prostřednictvím *:material-button-cursor: Add Data*{: .outlined_code}.
3. V panelu *:material-tab: Contents*{: .outlined_code} rozbalte CAD soubor. Prozkoumejte typy geometrie a dostupné atributy či hladiny.
4. Vyberte některou dílčí CAD vrstvu, např. **Polyline**, a zkontrolujte její prostorové umístění a souřadnicový systém. Případné varování o chybějícím CRS je v této úloze očekávané.
5. Spusťte nástroj *:material-cog: Define Projection*{: .outlined_code} (případně z karty *:material-tab: CAD Data*{: .outlined_code}). Jako vstup zvolte příslušný CAD dataset a **přiřaďte skutečný CRS, v němž byly souřadnice vytvořeny**.
6. Pokud je výkres skutečně v S-JTSK, vyberte **S-JTSK / Krovak East North (EPSG:5514)**. Jestliže má zdroj jiný systém, je nutné přiřadit právě ten; systém mapy sám o sobě správnost CRS neurčuje.
7. Přibližte se na výkres přes *:material-button-cursor: Zoom To Layer*{: .outlined_code} a porovnejte jeho polohu s referenčními daty.

!!! success "Očekávaný výsledek"
    CAD výkres leží na správném místě vzhledem k referenční vrstvě. **Není nutné jej posouvat, otáčet ani vytvářet vlícovací body.** ArcGIS Pro pro CAD soubor obvykle vytvoří doprovodný soubor `.prj` obsahující definici CRS.

??? question "K zamyšlení"
    Co by se stalo, kdybychom výkresu omylem přiřadili jiný souřadnicový systém, než ve kterém byly jeho souřadnice vytvořeny? Změnily by se souřadnice samotných prvků?

### Úloha B: DXF v lokálních souřadnicích – areál ČVUT v Dejvicích

**Vstupní data:** DXF výkres skutečných půdorysů budov v okolí kampusu ČVUT v Dejvicích, záměrně převedený do **lokálních souřadnic**. Pro kontrolu polohy využijeme referenční data stavebních objektů RÚIAN nebo ortofoto.

**Cíl:** Prostorově umístit výkres do mapy pomocí odpovídajících bodů na CAD výkresu a v referenční mapě.

**Postup:**

1. V nové mapě nastavte *:material-form-dropdown: Coordinate Systems*{: .outlined_code} na **S-JTSK / Krovak East North (EPSG:5514)** a přidejte referenční data budov v okolí ČVUT v Dejvicích.
2. Načtěte DXF s lokálními souřadnicemi. Pomocí *:material-button-cursor: Zoom To Layer*{: .outlined_code} si prohlédněte jeho geometrii. Porovnejte souřadnice nebo polohu se skutečným územím.
3. Vyberte jednu dílčí CAD vrstvu (například **Polyline** nebo **Polygon**) v panelu *:material-tab: Contents*{: .outlined_code}. **Nevybírejte pouze nadřazenou skupinovou vrstvu CAD.**
4. Na kartě *:material-tab: CAD Data*{: .outlined_code} spusťte *:material-cog: Define Projection*{: .outlined_code} a pro účely výsledného umístění zvolte **S-JTSK / Krovak East North (EPSG:5514)**. Tento krok sám výkres do Dejvic **nepřesune**: lokální souřadnice zatím neodpovídají souřadnicím S-JTSK.
5. Na kartě *:material-tab: CAD Data*{: .outlined_code} klikněte na *:material-button-cursor: Georeference*{: .outlined_code}. Pokud je výkres mimo mapový výřez, použijte *:material-button-cursor: Move To Display*{: .outlined_code} pro jeho přibližné umístění do aktuálního výřezu.
6. V případě potřeby použijte nástroje *:material-button-cursor: Move*{: .outlined_code}, *:material-button-cursor: Rotate*{: .outlined_code} a *:material-button-cursor: Scale*{: .outlined_code}, abyste výkres orientačně zarovnali s referenční mapou.
7. Klikněte na *:material-button-cursor: Add Control Points*{: .outlined_code}. Vyberte dobře rozpoznatelný bod na výkresu (**zdroj**) a odpovídající bod na referenční mapě (**cíl**), například roh budovy. Vytvořte **alespoň dvě dvojice odpovídajících bodů**, ideálně vzdálených od sebe, a zkontrolujte, že nepoužíváte chybně identifikované rohy.
8. Pomocí *:material-button-cursor: Apply*{: .outlined_code} aktualizujte umístění a výsledek porovnejte s referenční vrstvou. Podle potřeby upravte vlícovací body v *:material-tab: Control Point Table*{: .outlined_code}.
9. Uložte transformaci pomocí *:material-button-cursor: Save*{: .outlined_code} na kartě *:material-tab: Georeference*{: .outlined_code}. ArcGIS Pro uloží transformační informace do doprovodného souboru `.wld3` a původní DXF geometrii nepřepisuje.
10. Ověřte umístění také podle dalších rohů budov, které jste nepoužili při vytváření vlícovacích bodů.

!!! tip "Jak vybrat vlícovací body"
    Přednostně vybírejte **výrazné a stabilní rohy budov**, které lze jednoznačně určit v obou datech. Body by měly být rozmístěny po celé ploše výkresu, nikoli těsně vedle sebe. Přesnost ověření závisí také na přesnosti referenčních dat.

!!! success "Očekávaný výsledek"
    Půdorysy budov z lokálního CAD výkresu se překrývají s odpovídajícími stavbami v referenční mapě. Na rozdíl od úlohy A nestačilo pouze definovat CRS: bylo nutné také **určit prostorovou transformaci**.

### Porovnání obou postupů

| | Úloha A – známé skutečné souřadnice | Úloha B – lokální souřadnice |
|---|---|---|
| Souřadnice odpovídají skutečné poloze | Ano | Ne |
| Je potřeba definovat CRS | Ano | Ano, pro cílové umístění |
| Je potřeba georeferencování | Ne | Ano |
| Hlavní nástroj | *Define Projection* | *Georeference*, *Add Control Points* |
| Výsledná doprovodná informace | `.prj` | `.prj` + `.wld3` |

??? question "Kontrolní otázky"
    1. Jaký je rozdíl mezi **souřadnicemi prvku** a **souřadnicovým referenčním systémem**?
    2. Proč úloze A stačí nástroj *Define Projection*, zatímco úloha B vyžaduje georeferencování?
    3. Jaký je rozdíl mezi funkcemi *Define Projection* a *Project*?
    4. K čemu slouží soubory `.prj` a `.wld3` u CAD dat?
    5. Proč je vhodné kontrolovat umístění výkresu i na bodech, které nebyly použity pro georeferencování?

__Další informace:__
{: align=center }

[<span>pro.arcgis.com</span><br>Introduction to CAD data](https://doc.esri.com/en/arcgis-pro/latest/help/data/cad/what-is-cad-data.html){ .md-button .md-button--primary .server_name .external_link_icon_small target="_blank" }
[<span>pro.arcgis.com</span><br>Geospatial position of CAD and BIM data](https://doc.esri.com/en/arcgis-pro/latest/help/data/cad/geospatial-position-of-cad-and-bim-data.html){ .md-button .md-button--primary .server_name .external_link_icon_small target="_blank" }
[<span>pro.arcgis.com</span><br>Georeference CAD data](https://doc.esri.com/en/arcgis-pro/latest/help/data/cad/georeferencing-cad-data.html){ .md-button .md-button--primary .server_name .external_link_icon_small target="_blank" }
{: .button_array }
