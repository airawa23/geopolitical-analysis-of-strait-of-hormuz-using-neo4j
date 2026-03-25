# 🌍 Strait of Hormuz Geopolitical Graph Analysis

## 📌 Overview
This project analyzes the geopolitical network of the Strait of Hormuz using graph-based methods with Neo4j.  
The goal is to identify key countries and strategic bottlenecks in global energy and trade flows.

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
```

---

## 📊 Analysis

### 1. Degree Centrality
Measures how many direct connections a node has.

```cypher
CALL gds.degree.stream('geopolitikGraph')
YIELD nodeId, score
WITH gds.util.asNode(nodeId) AS n, score
WHERE 'Country' IN labels(n)
RETURN n.name AS Country, score AS DegreeCentrality
ORDER BY score DESC;
```

---

### 2. Betweenness Centrality
Identifies nodes that act as bridges in the network.

```cypher
CALL gds.betweenness.stream('geopolitikGraph')
YIELD nodeId, score
WITH gds.util.asNode(nodeId) AS n, score
WHERE 'Country' IN labels(n)
RETURN n.name AS Country, score AS BetweennessCentrality
ORDER BY score DESC;
```

---

## 🔍 Key Insights

- Iran and Saudi Arabia have the highest betweenness centrality → acting as major geopolitical bottlenecks  
- United States plays a strategic role as a global connector  
- China, India, and Indonesia act as endpoints rather than intermediaries  

This indicates a high concentration of geopolitical power in the Strait of Hormuz region.

---

## 🚀 How to Run

1. Import your dataset into Neo4j  
2. Run the graph projection query  
3. Execute centrality analysis queries  
4. Interpret results using Neo4j Browser  

---

## 📥 Clone Repository

```bash
git clone https://github.com/airawa23/geopolitical-analysis-of-strait-of-hormuz-using-neo4j.git
```

---

## 📸 Example Output
(Add your Neo4j graph screenshots here)

---

## 👤 Author
Team
