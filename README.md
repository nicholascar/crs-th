# CRS Thesaurus in SKOS
This is the Commonwealth Record Series (CRS)' thesauruses of government functions delivered as [SKOS vocabularies](https://www.w3.org/TR/skos-primer/).

The CRS database is maintained by the [National Archives of Australia](http://naa.gov.au) to keep track of the archiving of records from government persons and organisations and [RDF](https://www.w3.org/RDF/) / [OWL](https://www.w3.org/TR/owl2-overview/) implementations of its agency listings is modelled by the [CRS Ontology](https://github.com/CSIRO-enviro-informatics/crs-ont). Content according to the ontology will soon be delivered online via the [Longitudinal Spine of Government Functions' data portal](http://db.longspine.cat) (not public yet).

**NOTE: This thesaurus information is in test mode until this notice is removed**

## Files in this repository
* **[README.md](README.md)** - this file
* **[LICENSE](LICENSE)** - the license deed for this repository; Creative Commons v4.0 International
* **CRS Thesaurus**:
  * **[crs-th.xlsx](crs-th.xlsx)** - Excel workbook used to convert tabular CRS Thesaurus Terms to RDF. Includes many term definitions & term relations
  * **[crs-th-raw.ttl](crs-th-raw.ttl)** - raw RDF version of the CRS Thesaurus terms, taken from Excel & copy 'n pasted
  * **[crs-th.ttl](crs-th.ttl)** - the CRS Thesaurus Terms in RDF (turtle)
* **CRS Thesaurus Terms List 31**:
 * **[crs-th-31.xlsx](crs-th-31.xlsx)** - Excel workbook used to convert tabular CRS Thesaurus Terms List 31 to RDF. Contains all CRS Terms, not just List 31. Includes functions to transform the original Excel to RDF text
 * **[crs-th-31-raw.ttl](crs-th-31-raw.ttl)** - raw RDF version of the List 31 terms, taken from Excel & copy 'n pasted
 * **[crs-th-31.ttl](crs-th-31.ttl)** - the CRS Thesaurus Term List 31 in RDF (turtle)


## Original CRS v. CRS in SKOS
The original (still current) CRS information is stored in an Oracle database within the National Archives of Australia (NAA) as a table of terms. Rows from the table, VALID_THESAURUS_TERMS, look like this:

Classification ID | Term | Date Modified
--|--|--
31 | SOCIAL CLUB SUPPORT | 18/11/1999 0:00
31 | SOCIAL JUSTICE AND EQUITY | 15/11/1999 0:00
31 | SOIL PRESERVATION PROGRAMS | 15/11/1999 0:00
31 | SPATIAL INFORMATION RESEARCH | 17/11/1999 0:00
31 | ... | ...

The Classification ID is used to distinguish CRS Thesaurus terms from other thesauri such as earlier versions of [AGIFT](data.naa.gov.au/def/agift) and physical artefact types. Several other columns of information are also stored about terms, such as who in the NAA entered them. No term hierarchy, definitions, explanatory notes or other metadata are given for terms. There are 578 terms in total.

This information is contained within [crs-th-31.xlsx](crs-th-31.xlsx).

There are also other tables/files of data at NAA not stored directly in the CRS database, some of which contain term hierarchy and other relations information. The spreadsheet [crs-th.xlsx](crs-th.xlsx) is one such file. It contains CRS Thesaurus terms, definitions & term relations.

### SKOS structuring
#### CRS Thesaurus Terms
In this SKOS implementation of the CRS Thesaurus, the following conversions have been made, all of which are visible in column conversions in [crs-th.xlsx](crs-th.xlsx):

* *URI IDs* have been made using lowercase, punctuation-replaced, versions of terms
* *SKOS prefLabels* have been made using title (proper) case versions of terms
* *SKOS relations*:
  * 'EQ'-related terms have been interpreted thus: `A EQ B` == `<A> dct:isReplacedBy <B> ; <A> skos:broader <B> .`
  * 'NT'-related terms have been interpreted thus: `A NT B` == `<A> skos:narrower <B>`
  * 'RT'-related terms have been interpreted thus: `A RT B` == `<A> skos:related <B>`
  * 'SN'-related terms have been interpreted thus: no interpretation
  * 'VVT'-related terms have been interpreted thus: `A VTT` == `<A> skos:topConceptOf <Concept Scheme> .`


#### CRS Thesaurus Terms List 31
In this SKOS implementation of the CRC Thesaurus Term List 31, two levels of hierarchy have been introduced, so where in the original CRC Thesaurus you have terms like:

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

These 20 concepts are the *top concepts* of this SKOS implementation with the original 578 being second-level concepts. Due to SKOS' mechanics, both top- and second-level concepts may be used directly but.

### Other text changes
In this implementation, title case has been used so rather than *WATER CONSERVATION PLANS*, we have *Water Conservation Plans*.

All concepts' labels (in SKOS their preferred labels of *prefLabels*) are indicated as being in English.

Also, basic definitions for the top concepts have been added.

The term *ACCOMODATION SERVICES*, an incorrectly spelled, duplicative version of *ACCOMMODATION SERVICES* has been removed.

### URIs and access
Concepts have all been allocate individual persistent web addresses ([URI](https://en.wikipedia.org/wiki/Uniform_Resource_Identifier)s) for direct use. URIs consist of a base and an ID portion, for example the AGIFT term "General insurance"'s URI is [`https://data.naa.gov.au/def/agift/General-insurance`](https://data.naa.gov.au/def/agift/General-insurance) where the base is `https://data.naa.gov.au/def/agift/` and the ID is `General-insurance`.

Initially, CRS Thesaurus & Term List 31 terms have been used to create URI IDs by replacing spaces with hyphens and casting to lower case, so *WATER CONSERVATION PLANS* becomes `water-conservation-plans`.

The URI base is initially set to `http://test.linked.data.gov.au/def/crs-th/` for CRS Thesaurus & `http://test.linked.data.gov.au/def/crs-th-31/` for Term List 31 terms in for testing purposes. This uses the testing part of the [Australian Government Linked Data Working Group](http://www.linked.data.gov.au)'s `linked.data.gov.au` persistent domain, `/def/` to indicate a *definitional resource* and *crs-th* as a unique short code for the CRS Thesaurus.

Using base + ID, we have a URI for *WATER CONSERVATION PLANS* being:  
* [`http://test.linked.data.gov.au/def/crs-th/water-conservation-plans`](http://test.linked.data.gov.au/def/crs-th-31/water-conservation-plans)

The thesaurus (usually termed a *vocabulary* in SKOS) for CRS Thesaurus & Term List 31 as wholes are available online at:  
* [`http://test.linked.data.gov.au/def/crs-th`](http://test.linked.data.gov.au/def/crs-th)
* [`http://test.linked.data.gov.au/def/crs-th-31`](http://test.linked.data.gov.au/def/crs-th-31)

## Data & access
While in testing, the up-to-date copies of these vocabularies are stored in this code repository in the files [crs-th.ttl](crs-th.ttl) & [crs-th-31.ttl](crs-th-31.ttl). This point-of-truth may move as NAA systems take over.


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
