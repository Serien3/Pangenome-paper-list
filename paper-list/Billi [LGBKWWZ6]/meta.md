---
key: LGBKWWZ6
version: 10
itemType: preprint
title: 'Billi: Accurate and Scalable Bubble Detection in Pangenome Graphs'
abstractNote: A key application of pangenome graphs is the characterization of small and large genomic variants by enumerating bubble-like structures in the graph. Several formalizations of bubbles have been proposed. Superbubbles and ultrabubbles are two such formalizations, but both exclude cyclic subgraphs. Representing cyclic structures is essential for capturing complex genomic variation, such as inversions. Other definitions that accommodate cycles do not guarantee that overlapping bubbles are strictly nested. This makes it difficult to organize variants hierarchically and distinguish complex variants from their constituent subvariants. We introduce two formalizations, called panbubble and hairpin, that accommodate cyclic subgraphs. We prove that both satisfy the strict nesting property. In our theoretical analysis and algorithm design, we leverage an auxiliary undirected graph representation derived from the bidirected pangenome graph, enabling us to exploit established graph-theoretic
  algorithms and properties. We then present an exact O(|V|^2(|V| + |E|)-time algorithm for detecting all panbubbles and hairpins in a bidirected graph G = (V, E). In addition, we propose a heuristic that produces the same output as the exact algorithm on all tested graphs and scales to both the first and second releases of the Human Pangenome Reference Consortium. We implemented our algorithms in the tool Billi. At a known recurrent inversion locus on the human Y chromosome, Billi recovers the inversion together with its nested variants, whereas existing bubble-detection methods miss part of the variation or fail to correctly represent the nesting relationships among variants.
date: '2026-10-16'
language: en
shortTitle: Billi
libraryCatalog: bioRxiv
url: https://www.biorxiv.org/content/10.1101/2025.11.21.689636v2
accessDate: '2026-10-19T03:15:02Z'
rights: © 2026, Posted by openRxiv. This pre-print is available under a Creative Commons License (Attribution 4.0 International), CC BY 4.0, as described at http://creativecommons.org/licenses/by/4.0/
extra: 'ISSN: 2692-8205

  Pages: 2025.11.21.689636

  Section: New Results'
DOI: 10.1101/2025.11.21.689636
repository: bioRxiv
creators:
- Shreeharsha G. Bhat
- Daanish Mahajan
- Chirag Jain
zoteroTags: []
collections:
- BY9RK8U8
relations: {}
dateAdded: '2026-10-19T03:15:02Z'
dateModified: '2026-10-19T03:15:02Z'
---
