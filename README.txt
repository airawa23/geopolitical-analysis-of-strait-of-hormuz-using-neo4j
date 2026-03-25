# 🌍 Geopolitical Graph Analysis using Neo4j

## 📌 Overview

Project ini bertujuan untuk menganalisis hubungan geopolitik menggunakan graph database dengan Neo4j Graph Data Science (GDS).

Analisis difokuskan pada:

* Degree Centrality (koneksi langsung)
* Betweenness Centrality (peran sebagai penghubung)

---

## 🛠️ Tools & Technologies

* Neo4j
* Neo4j Graph Data Science (GDS)
* Cypher Query Language

---

## 📂 Dataset Structure

Node yang digunakan:

* Country
* Company
* Economy
* Location
* Transport

Relasi:

* Menggunakan semua tipe relasi (`*`)

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

## 📊 Analysis Queries

### Degree Centrality

```cypher
CALL gds.degree.stream('geopolitikGraph')
YIELD nodeId, score
WITH gds.util.asNode(nodeId) AS n, score
WHERE 'Country' IN labels(n)
RETURN n.name AS Country, score AS DegreeCentrality
ORDER BY score DESC;
```

### Betweenness Centrality

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

* **Iran & Arab Saudi** memiliki betweenness centrality tertinggi → berperan sebagai bottleneck utama
* **Amerika Serikat** berperan sebagai penghubung strategis global
* Negara seperti **China, India, Indonesia** berperan sebagai endpoint (bukan penghubung utama)

---

## 🚀 How to Run

1. Import dataset ke Neo4j
2. Jalankan graph projection
3. Jalankan query centrality
4. Analisis hasil

---

## 📥 Clone Repository

```bash
git clone https://github.com/USERNAME/geopolitical-graph-analysis.git
```

---

## 👤 Author

Team
