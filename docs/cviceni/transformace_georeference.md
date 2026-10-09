## Typy transformací při georeferencování rastrových dat

Při georeferencování rastru propojujeme **vlícovací body** (*control points*) na původním obrázku s odpovídajícími body v referenčních datech. Zvolená transformační metoda určuje, jakým způsobem se rastr posune, otočí, změní měřítko nebo geometricky deformuje.

| Transformace (ArcGIS Pro) | Min. počet vlícovacích bodů | Co umožňuje | Typické použití |
| :--- | :---: | :--- | :--- |
| **Zero-order Polynomial** (posun) | **1** | Pouze posun rastru v osách X a Y; zachovává měřítko, orientaci i tvar. | Rastr má již správné měřítko a orientaci, ale je mírně posunutý. |
| **Similarity Polynomial** (podobnostní) | **3** | Posun, otočení a **stejnou změnu měřítka** v obou směrech; zachovává úhly a poměry délek. | Obraz je správně geometricky utvářený, ale má jinou polohu, orientaci nebo velikost. |
| **1st Order Polynomial (Affine)** (afinní) | **3** | Posun, otočení, rozdílnou změnu měřítka v osách a zkosení; přímky zůstávají přímkami a rovnoběžnost se zachovává. | **Nejběžnější výchozí volba** pro skenované mapy a letecké snímky bez výrazných lokálních deformací. |
| **Projective** (projektivní) | **4** | Perspektivní deformaci: přímky zůstávají přímkami, ale původně rovnoběžné linie již nemusí být rovnoběžné. | Šikmé snímky nebo fotografie pořízené z perspektivy. |
| **2nd Order Polynomial** (polynomická 2. řádu) | **6** | Nelineární zakřivení a deformaci obrazu včetně ohýbání původně přímých linií. | Mapy nebo snímky s plynulými, složitějšími geometrickými deformacemi. |
| **3rd Order Polynomial** (polynomická 3. řádu) | **10** | Ještě složitější nelineární deformaci než transformace 2. řádu. | Výrazně deformované historické mapy; vyžaduje kvalitně rozmístěné vlícovací body. |
| **Adjust** (kombinovaná) | **3** | Kombinuje celkové polynomické přizpůsobení s lokálními úpravami založenými na triangulaci (TIN). | Když je potřeba vyvážit celkové přizpůsobení mapy a přesnost ve vybraných místech. |
| **Spline** (pružná / lokální) | **10** | Lokálně „natahuje“ rastr tak, aby vlícovací body odpovídaly přesně; mezi nimi může docházet k výrazným deformacím. | Silně nepravidelně deformované podklady, u kterých je prioritou shoda v kontrolních bodech. |

<figure markdown>
  ![Ukázka deformace původního rastru při využití polynomické transfformace I., II. a III. řádu](../assets/cviceni2/georef_transformace.gif){ width="100%" }
  <figcaption>Ukázka deformace původního rastru při využití polynomické transfformace I., II. a III. řádu. Zdroj: [ArcGIS Pro](https://doc.esri.com/en/arcgis-pro/latest/help/data/imagery/overview-of-georeferencing.html)</figcaption>
</figure>

!!! tip "Jakou transformaci vybrat?"
    Pro běžné cvičení začněte metodou **1st Order Polynomial (Affine)**. Pokud má být zachován původní tvar rastru, porovnejte výsledek se **Similarity Polynomial**. Vyšší řády a **Spline** používejte pouze tehdy, pokud to vyžaduje charakter deformace a máte dostatek kvalitních, rovnoměrně rozmístěných vlícovacích bodů.

!!! warning "Malá chyba RMS ještě neznamená správné georeferencování"
    Metody **Spline** nebo **Adjust** mohou vykazovat velmi malé odchylky ve vlícovacích bodech, ale rastr může být mezi nimi výrazně deformovaný. Vždy kontrolujte také polohu **nezávislých bodů**, které nebyly použity při výpočtu transformace, a vizuální soulad s referenční mapou.

!!! info "Pozor na dva různé procesy"
    **Geometrická transformace** určuje prostorové umístění a deformaci rastru. **Převzorkování (resampling)** následně stanovuje hodnoty pixelů ve výsledné rastrové mřížce (například *Nearest Neighbor*, *Bilinear* nebo *Cubic*). Jde o dva odlišné kroky.

**Další informace:**

- [Esri: Overview of georeferencing](https://doc.esri.com/en/arcgis-pro/latest/help/data/imagery/overview-of-georeferencing.html)
- [Esri: Georeference a raster to a referenced layer](https://doc.esri.com/en/arcgis-pro/latest/help/data/imagery/georeferencing-a-raster-to-a-referenced-layer.html)
