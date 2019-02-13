# CRS Thesaurus in SKOS
This is the Commonwealth Record Series (CRS)' thesaurus of government functions delivered as a [SKOS vocabulary](https://www.w3.org/TR/skos-primer/). 

The CRS is maintained by the [National Archives of Australia](http://naa.gov.au) to keep track of the archiving of records from government persons and organisations and an [RDF](https://www.w3.org/RDF/) / [OWL](https://www.w3.org/TR/owl2-overview/) version of the CRS is modelled by the [CRS Ontology](https://github.com/CSIRO-enviro-informatics/crs-ont) and content according to which will likely soon be delivered online.


## Origial CRS v. CRS in SKOS
The original (still current) CRS information is stored in an Oracle database within the National Archives of Australia (NAA) as a table of terms, rows of which look like this:

Classification ID | Term | Date Modified
--|--|--
31 | SOCIAL CLUB SUPPORT | 18/11/1999 0:00
31 | SOCIAL JUSTICE AND EQUITY | 15/11/1999 0:00
31 | SOIL PRESERVATION PROGRAMS | 15/11/1999 0:00
31 | SPATIAL INFORMATION RESEARCH | 17/11/1999 0:00
31 | ... | ...

The Classification ID is used to distinguish CRS Thesaurus terms from other thesauri such as earlier versions of [AGIFT](data.naa.gov.au/def/agift) and physical artefact types. Several other colums of information are also stored about terms, such as who in the NAA entered them. No term hierarchy, definitions, explanatory notes or other metadata are given for terms. There are 578 terms in total.

In this SKOS version of the CRC Thesuarus, 





## License
This ontology and all other content in this repository are licensed under the [Creative Commons Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/) (local copy of deed: [LICENSE](LICENSE)).


## Contacts
SKOS Vocabulary creator:  
**Nicholas Car**  
*Senior Experimental Scientist*  
CSIRO Land & Water, Brisbane, Australia    
<nicholas.car@csiro.au>  
<http://orcid.org/0000-0002-8742-7730>  

Contributors:

**David Hearder**  
*a/g Assistant Director*  
Commonwealth Information Policy  
Collection Management  
National Archives of Australia 
