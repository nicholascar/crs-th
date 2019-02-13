# CRS Thesaurus in SKOS
This is the Commonwealth Record Series (CRS)' thesaurus of government functions delivered as a [SKOS vocabulary](https://www.w3.org/TR/skos-primer/). 

The CRS is maintained by the [National Archives of Australia](http://naa.gov.au) to keep track of the archiving of records from government persons and organisations and an [RDF](https://www.w3.org/RDF/) / [OWL](https://www.w3.org/TR/owl2-overview/) implementation of the CRS is modelled by the [CRS Ontology](https://github.com/CSIRO-enviro-informatics/crs-ont) and content according to which will likely soon be delivered online.

**NOTE: This thesaurus is in test mode until this notice is removed**


## Original CRS v. CRS in SKOS
The original (still current) CRS information is stored in an Oracle database within the National Archives of Australia (NAA) as a table of terms, rows of which look like this:

Classification ID | Term | Date Modified
--|--|--
31 | SOCIAL CLUB SUPPORT | 18/11/1999 0:00
31 | SOCIAL JUSTICE AND EQUITY | 15/11/1999 0:00
31 | SOIL PRESERVATION PROGRAMS | 15/11/1999 0:00
31 | SPATIAL INFORMATION RESEARCH | 17/11/1999 0:00
31 | ... | ...

The Classification ID is used to distinguish CRS Thesaurus terms from other thesauri such as earlier versions of [AGIFT](data.naa.gov.au/def/agift) and physical artefact types. Several other colums of information are also stored about terms, such as who in the NAA entered them. No term hierarchy, definitions, explanatory notes or other metadata are given for terms. There are 578 terms in total.

### SKOS structuring
In this SKOS implemetation of the CRC Thesuarus, two levels of hierarchy have been introduced, so where in the original CRC Thesuarus you have terms like:

* WATER CONSERVATION PLANS
* WATER QUALITY MONITORING
* WATER RESOURCES
* WATER SUPPLY
* WATER USAGE MANAGEMENT
* WATERWAY MANAGEMENT

Now you have a 2-level concept hierarchy like:

* WATER
  * WATER CONSERVATION PLANS
  * WATER QUALITY MONITORING
  * WATER RESOURCES
  * WATER SUPPLY
  * WATER USAGE MANAGEMENT
  * WATERWAY MANAGEMENT 

So WATER has been added and the water-related concepts placed under it. Also added are:

* Arts
* Businesses
* Health Services
* Community
* Disasters
* Emergencies
* Employment
* Energy
* Health
* Hospitals
* Indigenous
* Information
* International
* Land
* Military
* Rail
* Roads
* Small Business
* Workplace

These 20 concepts are the *top concepts* of this SKOS implemenation with the original 578 being second-level concepts. Due to SKOS' mechanics, both top- and second-level concepts may be used directly but.

### Other text changes
In this implementation, title case has been used so rather than *WATER CONSERVATION PLANS*, we have *Water Conservation Plans*. 

All concepts' labels (in SKOS their preferred labels of *prefLabels*) are indicated as being in English.

Also, basic definitions for the top concepts have been added.

### URIs and access
Concepts have all been allocate individual persistent web addresses ([URI](https://en.wikipedia.org/wiki/Uniform_Resource_Identifier)s) for direct use. URIs consist of a base and an ID portion, for example the AGIFT term "General insurance"'s URI is [`https://data.naa.gov.au/def/agift/General-insurance`](https://data.naa.gov.au/def/agift/General-insurance) where the base is `https://data.naa.gov.au/def/agift/` and the ID is `General-insurance`.

Initially, the concept prefLabels have been used to create URI IDs by replacing spaces with hyphens and casting to lower case, so *Water Conservation Plans* becomes `water-conservation-plans`.

The URI base is initally set to `http://test.linked.data.gov.au/def/crs-th/` in for testing purposes. This uses the testing part of the [Australin Government Linked Data Working Group](http://www.linked.data.gov.au)'s `linked.data.gov.au` persistent domain, `/def/` to indicate a *definitional resource* and *crs-th* as a unique short code for the CRS Thesaurus.

Using base + ID, we have a URI for *Water Conservation Plans* being `http://test.linked.data.gov.au/def/crs-th/water-conservation-plans`.

The thesaurus (usually termed a *vocabulary* in SKOS) as a whole is available online at `http://test.linked.data.gov.au/def/crs-th`.

## Data & access
While in testing, the up-to-date copy of this vocabulary's content is stored in this code repository in the file [crs-th.ttl](crs-th.ttl). This point-of-truth may move as NAA systems take over.


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
