## 算法的trace

### 1. union_find

- quick find

![image-20241231150302067](C:\Users\党子清\AppData\Roaming\Typora\typora-user-images\image-20241231150302067.png)

​	![image-20250102143801924](C:\Users\党子清\AppData\Roaming\Typora\typora-user-images\image-20250102143801924.png)

- quick union

  ![image-20241231150523769](C:\Users\党子清\AppData\Roaming\Typora\typora-user-images\image-20241231150523769.png)
  
  ![image-20250102143831955](C:\Users\党子清\AppData\Roaming\Typora\typora-user-images\image-20250102143831955.png)
  
  - weighted quick union
  
  ![image-20250102144056059](C:\Users\党子清\AppData\Roaming\Typora\typora-user-images\image-20250102144056059.png)
  
  ![image-20250102144155917](C:\Users\党子清\AppData\Roaming\Typora\typora-user-images\image-20250102144155917.png)
  
  - path compression
  
    ![image-20250102144330851](C:\Users\党子清\AppData\Roaming\Typora\typora-user-images\image-20250102144330851.png)

### 2. sort

- selection sort

  ![image-20241231151332438](C:\Users\党子清\AppData\Roaming\Typora\typora-user-images\image-20241231151332438.png)

- insertion sort

  ![image-20250102144922178](C:\Users\党子清\AppData\Roaming\Typora\typora-user-images\image-20250102144922178.png)

  ![image-20241231151421673](C:\Users\党子清\AppData\Roaming\Typora\typora-user-images\image-20241231151421673.png)

- binary search

  ![image-20241231151512046](C:\Users\党子清\AppData\Roaming\Typora\typora-user-images\image-20241231151512046.png)

- merge sort

  - UP-DOWN


![image-20241231150804273](C:\Users\党子清\AppData\Roaming\Typora\typora-user-images\image-20241231150804273.png)

![image-20241231150853658](C:\Users\党子清\AppData\Roaming\Typora\typora-user-images\image-20241231150853658.png)

- quick sort

  ![image-20241231151125400](C:\Users\党子清\AppData\Roaming\Typora\typora-user-images\image-20241231151125400.png)

![image-20241231151149087](C:\Users\党子清\AppData\Roaming\Typora\typora-user-images\image-20241231151149087.png)

![image-20250102145612010](C:\Users\党子清\AppData\Roaming\Typora\typora-user-images\image-20250102145612010.png)

improvement:当小数组时使用插入排序

![image-20250102150208461](C:\Users\党子清\AppData\Roaming\Typora\typora-user-images\image-20250102150208461.png)

### 3. priority queue

elementary implementation:

- unordered list
- ordered list
- heap

![image-20250102152049609](C:\Users\党子清\AppData\Roaming\Typora\typora-user-images\image-20250102152049609.png)

- **heapsort**

  ![image-20250102152250643](C:\Users\党子清\AppData\Roaming\Typora\typora-user-images\image-20250102152250643.png)

  ![image-20250102152351951](C:\Users\党子清\AppData\Roaming\Typora\typora-user-images\image-20250102152351951.png)

### BST

![image-20250102153125742](C:\Users\党子清\AppData\Roaming\Typora\typora-user-images\image-20250102153125742.png)

![image-20250102153233633](C:\Users\党子清\AppData\Roaming\Typora\typora-user-images\image-20250102153233633.png)

### 4. graph

- 拓扑排序

  ![image-20241231152759420](C:\Users\党子清\AppData\Roaming\Typora\typora-user-images\image-20241231152759420.png)

![image-20241231160315366](C:\Users\党子清\AppData\Roaming\Typora\typora-user-images\image-20241231160315366.png)

- kruskal算法

  ![image-20241231160708187](C:\Users\党子清\AppData\Roaming\Typora\typora-user-images\image-20241231160708187.png)

  - PRIM LAZY

    ![image-20241231202114978](C:\Users\党子清\AppData\Roaming\Typora\typora-user-images\image-20241231202114978.png)
    
    ![image-20241231160906166](C:\Users\党子清\AppData\Roaming\Typora\typora-user-images\image-20241231160906166.png)

- PRIM EAGER

  ![image-20241231161000333](C:\Users\党子清\AppData\Roaming\Typora\typora-user-images\image-20241231161000333.png)
  
  对edgeTo和distTo数组的更新操作：
  
  ![image-20241231201935895](C:\Users\党子清\AppData\Roaming\Typora\typora-user-images\image-20241231201935895.png)
  
  public class PrimMST {
  
  ```java
  private final EdgeWeightedGraph graph;
  
  // 存放最小生成树中的边
  private final Edge[] edgeTo;
  
  // 每条边对应的权重
  private final double[] distTo;
  
  private final boolean[] marked;
  
  private final IndexMinPQ<Double> pq;
  
  public PrimMST(EdgeWeightedGraph graph) {
      this.graph = graph;
      int vertex = graph.vertex();
      this.edgeTo = new Edge[vertex];
      this.marked = new boolean[vertex];
      this.pq = new IndexMinPQ<>(vertex);
      this.distTo = new double[vertex];
  	// 将权重数组初始化为无穷大
      for (int i = 0; i < vertex; i++)
          distTo[i] = Double.POSITIVE_INFINITY;
  
      for (int v = 0; v < vertex; v++)
          if (!marked[v]) prim(v);
  }
  
  private void prim(int s) {
  	// 将起点设为0.0并加入到优先队列
      distTo[s] = 0.0;
      pq.insert(s, distTo[s]);
      while (!pq.isEmpty()) {
  		// 取出权重最小的边,优先队列中存的顶点是与树相连的非树顶点,
  		// 同时它也是下一次要加入到树中的顶点
          int v = pq.delMin();
          scan(v);
      }
  }
  
  private void scan(int v) {
  	// 将顶点加入到树中
      marked[v] = true;
  
      for (Edge e : graph.adj(v)) {
          int w = e.other(v);
  		// 忽略失效边
          if (marked[w]) continue;
  		// 如果w与连接树顶点的边的权重小于其他w连接树顶点的边
  		// 则进行替换更新
          if (e.weight() < distTo[w]) {
              distTo[w] = e.weight();
              edgeTo[w] = e;
              if (pq.contains(w))
                  pq.decreaseKey(w, distTo[w]);
              else
                  pq.insert(w, distTo[w]);
          }
      }
  }
  
  public Iterable<Edge> edges() {
      Queue<Edge> mst = new ArrayDeque<>();
      for (int v = 0; v < edgeTo.length; v++) {
          Edge e = edgeTo[v];
          if (e != null) {
              mst.add(e);
          }
      }
      return mst;
  }
  
  public double weight() {
      double weight = 0.0;
      for (Edge e : edges())
          weight += e.weight();
      return weight;
  }
  ```
  
  }

### 5. stringsort

- key-index counting

  ![image-20241231162017731](C:\Users\党子清\AppData\Roaming\Typora\typora-user-images\image-20241231162017731.png) 

![image-20241231162045504](C:\Users\党子清\AppData\Roaming\Typora\typora-user-images\image-20241231162045504.png)

![image-20241231162101399](C:\Users\党子清\AppData\Roaming\Typora\typora-user-images\image-20241231162101399.png)

- lsd

  ![image-20241231162140371](C:\Users\党子清\AppData\Roaming\Typora\typora-user-images\image-20241231162140371.png)

- MSD

  ![image-20241231202514572](C:\Users\党子清\AppData\Roaming\Typora\typora-user-images\image-20241231202514572.png)

### 6. dijkstra

![image-20241231210426217](C:\Users\党子清\AppData\Roaming\Typora\typora-user-images\image-20241231210426217.png)

![image-20241231210530503](C:\Users\党子清\AppData\Roaming\Typora\typora-user-images\image-20241231210530503.png)

### 7.haffman encoding

![image-20241231211934488](C:\Users\党子清\AppData\Roaming\Typora\typora-user-images\image-20241231211934488.png)

- expanding

  ![image-20241231212011903](C:\Users\党子清\AppData\Roaming\Typora\typora-user-images\image-20241231212011903.png)

- constructing

  ![image-20241231212110996](C:\Users\党子清\AppData\Roaming\Typora\typora-user-images\image-20241231212110996.png)

### 8. LZW压缩

![image-20241231212244578](C:\Users\党子清\AppData\Roaming\Typora\typora-user-images\image-20241231212244578.png)

![image-20241231212317378](C:\Users\党子清\AppData\Roaming\Typora\typora-user-images\image-20241231212317378.png)

### 9. run_length encoding

![image-20241231212435633](C:\Users\党子清\AppData\Roaming\Typora\typora-user-images\image-20241231212435633.png)

![image-20241231212502495](C:\Users\党子清\AppData\Roaming\Typora\typora-user-images\image-20241231212502495.png)