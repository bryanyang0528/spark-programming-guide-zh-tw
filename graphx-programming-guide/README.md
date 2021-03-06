# Spark GraphX

## 概觀
GraphX是一個新的（alpha） Spark API，它用於圖形（Graph）和平行圖形（Graph-parallel）的計算。GraphX透過引入[Resilient Distributed Property Graph](property-graph.md)：一種帶有頂點和邊屬性的有向多重圖，來擴展Spark RDD。為了支援圖形的運算，GraphX公開一系列基本運算子（例如：subGraph、joinVertices、aggregateMessages）和Pregel API的優化。此外，GraphX也持續增加圖形演算法還有簡化分析圖形的工具（Builder）。

## 動機
從社群媒體到語言模型，數量和重要性不斷成長的圖形結構資料推動了許多`graph-parallel`系統（例如：[Giraph](http://giraph.apache.org/)和 [GraphLab](https://dato.com/products/create/open_source.html)）的發展。
藉由限制可表示的運算型別和帶入新的技術來劃分和分配圖形，這些系統能夠有效率地執行複雜的圖形演算法，比一般的`data-parallel`的系統快很多。

![data parallel vs graph parallel](../img/data_parallel_vs_graph_parallel.png)

然而，透過這種限制可以大量的提高效能，但是很難表現典型圖形分析流程：建構圖形、修改結構或是表達橫跨多個圖形的運算中很多的重要階段。另外，如何看待資料取決於我們的目標，且相同的原始資料可能有許多不同的表格和圖形。

![Table and graph](../img/tables_and_graphs.png)

總結來講，圖形和表格之間經常需要夠夠互相轉換。然而，現存的圖形分析流程必須撰寫`graph-parallel`和`data- parallel`系統，導致大量資料的搬移和重複還有複雜的程式模型。

![Graph analytics pipeline](../img/graph_analytics_pipeline.png)

GraphX的目的就是將`graph-parallel`和`data-parallel`整合成一個系統中，而且只有一個整合後的API。GraphX允許使用者將資料視為一個圖形和集合（例如: RDDs），而不需要任何的資料搬移和複製。最新的 `graph-parallel` 系統，使得GraphX能夠優化圖形指令的執行。

* [入門](getting-started.md)
* [圖形特性](property-graph.md)
* [圖形運算子](graph-operators.md)
* [Pregel API](pregel-api.md)
* [圖形建構式](graph-builders.md)
* [頂點和邊的RDDs](vertex-and-edge-rdds.md)
* [圖形演算法](graph-algorithms.md)
* [範例](examples.md)
