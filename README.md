# Diplomová práca

## Tema

Graph-based querying and mutations of Linked Data

Cielom prace je analyzovat existujuce pristupy k autorizacii, query rewritingu a policy-based ochrane dat v prostredi grafovych a semantickych dat a na zaklade toho navrhnut vlastne riesenie vhodne pre existujucu architekturu postavenu na GraphQL, RDF a UltraGraphQL.

Aktualne sa praca sustreduje najma na:

- analyzu existujuceho riesenia v systeme Courses,
- studium generovania GraphQL rozhrani nad RDF datami,
- studium OBDA a policy-based pristupov,
- analyzu moznosti query rewritingu pre SPARQL,
- pripravu navrhu vlastneho modelu autorizacie/policies.

## Aktualny stav

K 15. maju 2026 je hotova uvodna analyza problemu a prehlad hlavnych suvisiacich pristupov. Zatial vyplyva, ze:

- existujuce pristupy ku generovaniu GraphQL rozhrania autorizaciu priamo neriesia,
- v starsom backendovom rieseni je autorizacia relationship-based a vyhodnocuje sa nad cestou medzi pouzivatelom a RDF instanciou,
- policy-based pristupy v OBDA su zaujimave, ale zameriavaju sa najma na citanie dat,
- query rewriting bude pravdepodobne potrebne riesit samostatne, pretoze existujuce nastroje nie je mozne jednoducho prevziat pre SPARQL -> SPARQL scenar.

## Kalendar a progres

### Februar 2026

- Zaciatok prace na teme a spresnenie problemu autorizacie nad grafovymi datami.
- Oboznamenie sa s existujucou architekturou a s tym, ze v systeme sa vyuziva UltraGraphQL.
- Zber podkladov a vyhladanie relevantnych prac k GraphQL, RDF, OBDA a autorizacii.

### Marec 2026

- Studium pristupov ku generovaniu GraphQL rozhrani nad semantickymi datami.
- Analyza clanku:
  - Huanyu Li et al.: Ontology-based GraphQL server generation for data access and data integration.
  - Lars Christoph Gleim et al.: Automatic Bootstrapping of GraphQL Endpoints for RDF Triple Stores.
- Zistenie, ze tieto pristupy sa sustreduju na generovanie rozhrania, nie na autorizaciu.

### Koniec marca - april 2026

- Studium existujuceho riesenia v diplomovej praci Milana Cifru.
- Identifikacia relationship-based autorizacie:
  - autorizacne pravidlo je zapisane ako cesta medzi `instanceIRI` a `userIRI`,
  - pri `GET` sa pravidla premietaju do casti `SPARQL WHERE`,
  - pri modifikaciach sa pravidla vyhodnocuju v backende.
- Studium Baluchovej prace a porovnanie s predchadzajucim riesenim.
- Zistenie, ze v Baluchovej praci je autorizacia hlavne navrhnuta a pripravena pre UGQL, ale nie plne dokoncena.

### April 2026

- Studium teoretickeho pozadia k `OBDA`.
- Analyza clanku:
  - Guohui Xiao et al.: Ontology-Based Data Access: A Survey.
- Oboznamenie sa s konceptmi:
  - ontologie,
  - mapovania,
  - query rewriting,
  - preklad dotazov nad ontologiou na dotazy nad zdrojovymi datami.

### Koniec aprila - zaciatok maja 2026

- Studium policy-based pristupov v OBDA.
- Analyza clankov:
  - Domenico Fabio Savo et al.: Controlled Query Evaluation in Ontology-Based Data Access.
  - Divya Baura, Diego Calvanese, Lorenzo Marconi: Implementing controlled query evaluation in OBDA.
- Zistenie, ze policies sa v tychto pristupoch integruju do vrstvy mappingov a query rewritingu.
- Zistenie, ze tieto pristupy podporuju najma citanie dat a neposkytuju hotove riesenie pre zapisove operacie.

### Maj 2026

- Prakticke skusanie nastroja `Ontop` a analyza moznosti znovupouzitia jeho query rewriting mechanizmu.
- Zistenie, ze Ontop je silno naviazany na `SPARQL -> SQL` pipeline a SQL mapping sa pouziva uz v skorej faze rewritingu.
- Zaver, ze pre potreby tejto prace nebude stacit priame prevzatie existujuceho rewritingu a bude potrebne navrhnut vlastny pristup.
- Studium rewriting algoritmov, najma:
  - `PerfectRef`,
  - `Presto`.
- Zistenie, ze pri vacsich a zlozitejsich dotazoch je potrebne hladat efektivnejsi alebo vhodnejsie prisposobeny pristup.


## Dalsie kroky

- formalizovat poziadavky na autorizaciu,
- navrhnut strukturu policies,
- rozhodnut, kde a ako sa budu policies vyhodnocovat,
- navrhnut prvy prototyp rewritingu alebo kontrolneho mechanizmu,
- pripravit implementacnu cast prace.
