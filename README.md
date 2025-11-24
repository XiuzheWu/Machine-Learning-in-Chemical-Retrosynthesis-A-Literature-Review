# Is Machine Learning Applicable in Retrosynthesis of Chemicals?

## 📖 Abstract
Retrosynthetic analysis—the process of breaking down complex molecules into simpler precursors—is fundamental to organic chemistry but traditionally relies on time-consuming manual expertise. This literature review explores the transformative role of Machine Learning (ML) in Computer-Assisted Synthesis Planning (CASP).

The review critically analyzes the evolution of three major algorithmic families: **Proof Number Search (PNS)**, **Monte Carlo Tree Search (MCTS)**, and **A* Search**. By comparing early implementations with modern advancements such as **DFPN-E**, **ReTReK**, and **RetroGraph**, this work evaluates their performance in terms of computational efficiency, success rate, and chemical plausibility. The findings highlight a significant shift from tree-based search structures to graph-based representations, which effectively address redundancy and scalability in modern synthetic planning.

## 🧠 Key Themes

The review is structured around the evolution of search strategies in chemical space:

* **Heuristic Search Optimization (PNS → DFPN-E)**
    * **Challenge:** Traditional Depth-First Proof-Number Search (DFPN) struggles with the "uneven branching" of chemical reaction trees, where molecule nodes have many options, but reaction nodes have few.
    * **Solution:** **DFPN-E** introduces heuristic edge initialization using neural networks to prioritize promising reactions, significantly reducing search time compared to standard MCTS and DFPN.

* **Data-Driven vs. Knowledge-Guided Search (MCTS → ReTReK)**
    * **Challenge:** Purely data-driven models like **3N-MCTS** prioritize statistical probability but often propose chemically impractical routes (e.g., ignoring stereochemistry or commercially unavailable starting materials).
    * **Solution:** **ReTReK** integrates domain-specific scoring functions (e.g., *Convergent Disconnection Score*, *Available Substances Score*) to guide the Monte Carlo search toward more practical and efficient synthetic pathways.

* **Tree vs. Graph Representations (A* → RetroGraph)**
    * **Challenge:** Tree-based methods like **Retro*** suffer from "intra-target" and "inter-target" redundancy, recalculating the same intermediate molecules multiple times.
    * **Solution:** **RetroGraph** utilizes a directed graph structure and Graph Neural Networks (GNNs). By treating retrosynthesis as a graph, it shares common intermediates across different routes, achieving a success rate of **99.47%** on benchmark datasets and outperforming previous methods.

## 📊 Visual Summary

![Tree and graph.jpg]
> **Figure:** Comparison of Tree (left) vs. Graph (right) structures. The graph representation (used in RetroGraph) eliminates redundant calculations by connecting shared intermediate nodes, whereas tree structures (used in Retro* and MCTS) often duplicate them.

## 📚 Key References

This review synthesizes findings from the following key studies:

* **[Planning chemical syntheses with deep neural networks and symbolic AI]** - (Segler et al., *Nature*, 2018)
    * *My Take:* The seminal paper establishing 3N-MCTS, proving ML can compete with human chemists in route design.
* **[Depth-first proof-number search with heuristic edge cost and application to chemical synthesis planning]** - (Kishimoto et al., 2019)
    * *My Take:* Introduced DFPN-E, demonstrating how heuristic edge weighting can fix the search imbalances in traditional PNS.
* **[Retro*: Learning Retrosynthetic Planning with Neural Guided A* Search]** - (Chen et al., 2020)
    * *My Take:* Applied the A* algorithm to retrosynthesis but highlighted the critical issue of computational redundancy in tree structures.
* **[RetroGraph: Retrosynthetic Planning with Graph Search]** - (Xie et al., *KDD*, 2022)
    * *My Take:* The state-of-the-art approach that treats retrosynthesis as a graph problem, drastically improving scalability and efficiency.
* **[WIRES Computational Molecular Science Review]** - (Zhong et al., 2023)
    * *My Take:* Provided the comprehensive benchmark data used to objectively compare the success rates of these algorithms.

---
