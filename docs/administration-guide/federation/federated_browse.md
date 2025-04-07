---
title: Federated Browse
layout: default
summary: Seamlessly discover ontologies locally and from other federated portals
status: Preliminary
nav_order: 2
parent: OntoPortal Federation
grand_parent: Administration Guide
permalink: /administration/federation/federated_browse
---

# Federated Browse
The introduction of federated browsing in the OntoPortal federation marks a significant enhancement in the way users explore ontologies and semantic artefacts. This feature allows users to seamlessly discover ontologies not only from the semantic artefact catalogue they are currently browsing but also from other federated portals. The total number of ontologies and artefacts gathered by all the 4-federated OntoPortals is currently 376! Federated results are integrated alongside local results, preserving the familiar interface while expanding the scope of discovery. All filters remain functional as the metadata model used by each portal are the sames. The functionality of the filters is however dependant of the quality fo the metadata served by each portal. Thanks to the federation of the Categories, numbers can be calculated with unified categories coming from each federated portals (only parent categories are retrieved from the remote catalogues). Note that Groups are not federated and stayed a mechanism to regroup artefacts only on the local catalogue. Similarly, private settings (i.e., the ability to acess private artefacts) are excluded as users accounts and ACLs are not yet federated.
Users can activate federation through a straightforward selector, and the visual design incorporates the portal's color code and small logos to clearly distinguish federated ontologies. The number of ontologies retrieved from each portal are automatically updated with filters or parameters selected.

![Federated Browse]({{site.figures_link}}/OntoPortal/federation/browse-federation.png)


When clicking on an ontology result, the user will either stay on the local catalogue if the ontology found is hosted locally or move to another portal in the federation if not. Duplicates are identified by matching acronyms and URIs, and only one unified ontology card is displayed, aggregating analytics like notes and projects and listing logos for the set of portals where the ontology can be found.
* If the duplicate ontology is found locally, the card will always feature the local information and allow users to continue locally to explore the artefact in the catalogue which intitated the query.
* If the duplicate ontology is not in local catalogue, the card will reflect the primary portal’s color. The primary (or canonical) portal for an ontology is found to be the one with the highest number of pull location references from other portals in the federation.

For performance scalability, the Browse page incrementally loads results from federated APIs; only local ontologies load by default followed by federated results if selected providing a seamless user experience while making aware to the users that additional content is being loaded.
