# Semestrální práce – Analýza území

## Zadání

Jsou zadána tato ORP:

- **Dobruška**
- **Nový Bor**
- **Mělník**
- **Strážnice**
- **Bystřice n. Pern.**
- **Kaplice**
- **Mariánské Lázně**
- **Chomutov**
- **Kladno**
- **Chotěboř**

Vaším úkolem je připravit mapový poster (infografiku), která se bude věnovat analýze území dané ORP s ohledem na vhodnost stavby tří objektů:

- nová **solární elektrárna** :material-solar-power-variant:{ .lg .middle } ,
- nová **rozhledna** :material-tower-fire:{ .lg .middle },
- nová **skládka** :material-dump-truck:{ .lg .middle }.

<hr class="level-1">
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


Plocha pro výstavbu solární elektrárny je považována za vhodnou, pokud její celkové bodové ohodnocení dosahuje **MIN. 7 BODŮ**.

Na základě výsledků analýzy vytvořte přehlednou vizualizaci zobrazující lokality vhodné pro výstavbu solární elektrárny v zadaném ORP, jednotlivé lokality rozlište do 3 kategorií dle vhodnosti podmínek *(např. méně vhodná lokalita (7 b.)/ vyhovující lokalita (8–9 b.)/ optimální lokalita (10 b.))*.

- **DATOVÉ ZDROJE:**

    [:material-layers: DMR5G ](https://ags.cuzk.gov.cz/arcgis2/rest/services/dmr5g/ImageServer){ .md-button .md-button--primary .button_smaller target="_blank"}
    [:material-layers: ZABAGED ]("''OrnaPudaAOstatniDaleNespecifikovanePlochy', 'TrvalyTravniPorost'' "){ .md-button .md-button--primary .button_smaller}
    {: .button_array style="justify-content:flex-start;"}


<hr class="level-1">

### :material-tower-fire:{ .lg .middle } **ROZHLEDNA**

Z 10 nejvyšších výškových bodů v zadaném ORP identifikujte **3 nejvhodnější lokality pro výstavbu rozhledny**{style="text-transform:uppercase;"}. Hlavním kritériem výběru lokality je viditelnost co největší plochy zadaného ORP. Maximální přípustná výška stavby je 35 m, přičemž pozorovací ochoz je ve výšce 32 m. Zjistěte, jaká je viditelnost významných budov (kostel, zámek, hrad).

Na základě výsledků analýzy vytvořte 3D scénu zobrazující vhodné lokality pro výstavbu rozhledny s modelovanou viditelností. Ve scéně můžete libovolně vyznačit budovy či významné krajinné prvky, které jsou z dané lokality viditelné. Volitelně můžete namodelovat i samotnou stavbu rozhledny.

- **DATOVÉ ZDROJE:**

    [:material-layers: DMP1G ](https://ags.cuzk.gov.cz/arcgis2/rest/services/dmp1g/ImageServer){ .md-button .md-button--primary .button_smaller target="_blank"}
    [:material-layers: Data50 ]("''KotovanyBod', 'Kostel', 'VezovitaStavba', 'Zamek', 'Zricenina', 'Hrad''"){ .md-button .md-button--primary .button_smaller}
    [:material-layers: ZABAGED ]("''KotovanyBod', 'BudovaJednotlivaNeboBlokBudov''"){ .md-button .md-button--primary .button_smaller}
    {: .button_array style="justify-content:flex-start;"}

<hr class="level-1">

### :material-dump-truck:{ .lg .middle } **SKLÁDKA**

#### Podmínky

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
| Vzdálenost k pozemním komunikacím | silnice III. tř. a vyšší max. 250 m daleko |

<hr class="level-1">

## OBECNĚ

- Výstup bude formou tištěného mapového posteru velikosti min. A2.
- Mimo vizualizací by měl poster obsahovat základní charakteristiku území ORP (rozloha, počet obyvatel a slovní popis území).
- Výstupy analýz budou doprovozeny textem interpretujícím výsledky.





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

## Termín
- **informační den** k semestrální práci proběhne 15. května, **do 31. května** se pak předpokládá **odevzdání**.
