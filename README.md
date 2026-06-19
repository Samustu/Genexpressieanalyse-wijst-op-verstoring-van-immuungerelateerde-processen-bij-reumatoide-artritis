
#  Transcriptomics-Analyse-van-Reumatoïde-artritis

##  Inleiding  
Reumatoïde artritis (RA) is een chronische auto-immuunziekte die wordt gekenmerkt door ontsteking van synoviaal weefsel en progressieve gewrichtsschade. Immuuncellen zoals T-cellen, B-cellen en macrofagen infiltreren het gewricht en veroorzaken ontstekingsprocessen en weefselafbraak (Miyabe et al., 2020). Chemokines en cytokines spelen hierbij een belangrijke rol doordat zij de activatie en migratie van immuuncellen reguleren (Miyabe et al., 2020).

RNA sequencing (RNA-seq) maakt het mogelijk om genexpressie op genome-wide niveau te analyseren en verschillen tussen ziekte en controle te identificeren. Deze techniek wordt veel toegepast om de moleculaire mechanismen achter complexe ziekten, zoals RA, beter te begrijpen (Love et al., 2014; Stephenson et al., 2018).

Het doel van dit project is om met behulp van RNA-seq data inzicht te verkrijgen in de moleculaire processen die betrokken zijn bij reumatoïde artritis. Hiervoor wordt eerst onderzocht welke genen significant differentieel geëxprimeerd zijn tussen RA-patiënten en gezonde controles. Vervolgens wordt met een Gene Ontology (GO)-analyse bepaald welke biologische processen verrijkt zijn onder deze differentieel geëxprimeerde genen. Ten slotte wordt gekeken welke genen en immuunmechanismen betrokken zijn binnen de KEGG pathway *Autoimmune Thyroid Disease* (hsa05320) en hoe deze samenhangen met de gevonden genexpressieveranderingen. Door deze analyses te combineren kan beter worden begrepen welke moleculaire en immunologische processen een rol spelen bij RA.

---

##  Methode  
Voor deze studie werd gebruikgemaakt van een publieke RNA-seq dataset van synoviaal weefsel afkomstig van 4 reumatoïde artritis (RA) patiënten en 4 gezonde controles. Uit het synoviale weefsel werd totaal RNA geïsoleerd en vervolgens gebruikt voor RNA sequencing (RNA-seq), waarmee genexpressie op genome-wide niveau kan worden bepaald (Fraenkel et al., 2021; Stephenson et al., 2018).

De bio-informatica-analyse is uitgevoerd in R (v4.4.1) en Bioconductor (v3.19). Ruwe sequencing reads werden uitgelijnd tegen het humane referentiegenoom (GRCh38) met *Rsubread* (v2.18.0) (Liao et al., 2019). Vervolgens werden reads toegewezen aan genen met *featureCounts* (v2.18.0), wat resulteerde in een count matrix (Liao et al., 2014).

Differentiële genexpressieanalyse werd uitgevoerd met *DESeq2* (v1.44.0). Genen met een adjusted p-value < 0,05 en een |log2 fold change| > 1 werden als significant beschouwd (Love et al., 2014).

Functionele analyse werd uitgevoerd met *goseq* (v1.56.0) voor Gene Ontology-verrijking (Young et al., 2010). KEGG pathway-analyse werd uitgevoerd met *KEGGREST* (v1.44.0) en gevisualiseerd met *pathview* (v1.44.0) (Kanehisa & Goto, 2000).


**Tabel 1.** Overzicht van de gebruikte RNA-seq samples. De dataset bestaat uit vier gezonde controles (Normal) en vier patiënten met reumatoïde artritis (Rheumatoid arthritis).
| Naam | Conditie |
|------|-----------|
| SRR4785819 | Normal |
| SRR4785820 | Normal |
| SRR4785828 | Normal |
| SRR4785831 | Normal |
| SRR4785979 | Rheumatoid arthritis |
| SRR4785980 | Rheumatoid arthritis |
| SRR4785986 | Rheumatoid arthritis |
| SRR4785988 | Rheumatoid arthritis |

---

##  Resultaten  
De differentiële genexpressieanalyse met DESeq2 identificeerde meerdere genen die significant verschilden tussen reumatoïde artritispatiënten en gezonde controles. Zowel opgereguleerde als neergereguleerde genen werden waargenomen, wat wijst op veranderingen in moleculaire processen die betrokken zijn bij de ziekte.

<p align="center">
  <img src="resultaten/Figuren/VolcanoplotWC.png" width="600">
</p>

**Figuur 1.** Volcano plot van de differentiële genexpressieanalyse tussen RA- en controlesamples.

Om de biologische betekenis van deze genexpressieveranderingen te onderzoeken, werd een Gene Ontology (GO)-analyse uitgevoerd. Hierbij werden voornamelijk immuungerelateerde biologische processen verrijkt, waaronder processen betrokken bij immuunrespons en activatie van immuuncellen.

<p align="center">
  <img src="resultaten/Figuren/GO_Results_plot.png" width="600">
</p>

**Figuur 2.** Top verrijkte GO-termen van de differentieel geëxprimeerde genen.

Vervolgens werd een KEGG pathway-analyse uitgevoerd. Binnen de pathway *Autoimmune Thyroid Disease* (hsa05320) werden veranderingen gevonden in genen die betrokken zijn bij antigeenpresentatie en T-celactivatie. Deze resultaten suggereren dat verstoring van adaptieve immuunprocessen een belangrijke rol speelt bij reumatoïde artritis.

<p align="center">
  <img src="resultaten/Figuren/hsa05320.pathview.png" width="600">
</p>

**Figuur 3.** KEGG pathway *Autoimmune Thyroid Disease* (hsa05320) met weergegeven genexpressieveranderingen.

---

##  Conclusie  

De resultaten tonen aan dat reumatoïde artritis sterk wordt gekenmerkt door ontregeling van het immuunsysteem. Met name processen zoals adaptieve immuunrespons, leukocytenactivatie en antilichaamvorming spelen een belangrijke rol.  

De analyse van T-cel activatie laat zien dat signaleringsroutes betrokken bij immuunactivatie verhoogd actief zijn bij RA-patiënten. Deze inzichten dragen bij aan een beter begrip van de ziekte en kunnen helpen bij het identificeren van nieuwe therapeutische doelwitten.  
