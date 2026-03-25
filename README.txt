# 🌍 Strait of Hormuz Geopolitical Graph Analysis

## 📌 Overview
This project analyzes the **geopolitical network of the Strait of Hormuz** using graph-based methods with Neo4j.  
The goal is to identify **key countries and strategic bottlenecks** in global energy and trade flows.

Graph analysis is performed using centrality metrics to understand the structure and influence of each entity.

---

## 🛠️ Tools & Technologies
- Neo4j
- Neo4j Graph Data Science (GDS)
- Cypher Query Language

---

## 📂 Data Model
### Nodes:
- Country
- Company
- Economy
- Location
- Transport

### Relationships:
- Multiple relationship types (`*`) representing geopolitical, economic, and trade connections

---

## ⚙️ Graph Projection

```cypher
CALL gds.graph.project(
  'geopolitikGraph',
  ['Company', 'Country', 'Economy', 'Location', 'Transport'],
  {
    RELASI_ALL: {
      type: '*',
      orientation: 'NATURAL'
    }
  }
);
