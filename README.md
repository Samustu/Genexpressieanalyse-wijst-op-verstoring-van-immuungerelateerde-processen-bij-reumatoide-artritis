
#  Transcriptomics-Analyse-van-Reumatoïde-artritis

##  Project Beschrijving  
Reumatoïde artritis (RA) is een chronische systemische auto-immuunziekte die wordt gekenmerkt door ontsteking van het gewrichtsslijmvlies (synovitis), wat leidt tot progressieve gewrichtsschade. De oorzaak van RA is multifactorieel en omvat genetische aanleg, omgevingsfactoren en een ontregeld immuunsysteem.  

In dit project wordt transcriptomics gebruikt om verschillen in genexpressie tussen RA-patiënten en gezonde controles te analyseren. Door middel van RNA-seq data worden genen en biologische pathways geïdentificeerd die betrokken zijn bij het ziekteproces.  

###  Doelstelling  
Het doel van deze studie is om:  
- differentieel geëxprimeerde genen te identificeren tussen RA en controles  
- inzicht te krijgen in betrokken biologische processen  
- relevante pathways te bepalen die een rol spelen in RA  

###  Dataset  
- 4 RA samples 
- 4 controle samples  
- RNA-seq paired-end data  
- Referentiegenoom: GRCh38  

---

##  Methode  

Voor deze analyse is gebruikgemaakt van RNA-seq data afkomstig van synoviaal weefsel van vier patiënten met reumatoïde artritis (RA) en vier gezonde controles. De ruwe sequencing reads (FASTQ-bestanden) zijn uitgelijnd tegen het humane referentiegenoom (GRCh38) met behulp van het *Rsubread* package (v2.18.0) in R (v4.4.1). Voor elke sample is een BAM-bestand gegenereerd, waarna deze bestanden zijn gesorteerd en geïndexeerd met het *Rsamtools* package (v2.20.0).  

Vervolgens is genquantificatie uitgevoerd met *featureCounts*, waarbij reads werden toegewezen aan genen op basis van een GTF-annotatiebestand. Dit resulteerde in een count matrix met het aantal reads per gen per sample.  

De differentiële expressieanalyse is uitgevoerd met *DESeq2* (v1.44.0), waarbij genen als significant werden beschouwd bij een adjusted p-value < 0.05 en |log2 fold change| > 1. Visualisatie is uitgevoerd met *EnhancedVolcano* (v1.22.0).  

Functionele analyse is uitgevoerd met *goseq* (v1.56.0) voor Gene Ontology en met *pathview* (v1.44.0) en *KEGGREST* (v1.44.0) voor pathway-analyse. Visualisaties zijn gemaakt met *ggplot2* (v3.5.1) en *dplyr* (v1.1.4).  

---

##  Resultaten  

De differentiële expressieanalyse toonde een groot aantal genen met significante veranderingen tussen RA en controles. De volcano plot laat zowel up- als downregulated genen zien, waarbij meerdere genen een hoge log2 fold change en lage p-waarde vertonen. Voorbeelden van sterk gereguleerde genen zijn *IGHV3-53*, *BCL2A1* en *PTGFR*, die betrokken zijn bij immuunresponsen.  

De Gene Ontology analyse laat zien dat de meeste differentieel geëxprimeerde genen betrokken zijn bij immuungerelateerde processen, zoals *immune response*, *leukocyte activation* en *adaptive immune response*. Daarnaast wordt een sterke verrijking gevonden voor het *immunoglobulin complex*, wat wijst op een belangrijke rol van B-cellen en antilichamen.  

### Volcano plot  
<p align="center">
  <img src="resultaten/Figuren/VolcanoplotWC.png" width="600"/>
</p>

### GO analyse (Top 10)  
<p align="center">
  <img src="resultaten/Figuren/GO_Results_plot.png" width="600"/>
</p>

### KEGG pathway (detail gebruikt in analyse)  
<p align="center">
  <img src="resultaten/Figuren/hsa05320.pathview.png" width="600"/>
</p>

---

##  Conclusie  

De resultaten tonen aan dat reumatoïde artritis sterk wordt gekenmerkt door ontregeling van het immuunsysteem. Met name processen zoals adaptieve immuunrespons, leukocytenactivatie en antilichaamvorming spelen een belangrijke rol.  

De analyse van T-cel activatie laat zien dat signaleringsroutes betrokken bij immuunactivatie verhoogd actief zijn bij RA-patiënten. Deze inzichten dragen bij aan een beter begrip van de ziekte en kunnen helpen bij het identificeren van nieuwe therapeutische doelwitten.  
