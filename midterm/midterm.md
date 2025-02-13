以下是 **CS5800 Lecture 2** 的中文笔记，包含核心知识点，并且专业术语以英文标注：

------

# **CS5800 讲座 2 笔记**

## **1. 算法的定义（What is an Algorithm）**

- **算法（Algorithm）** 是一系列计算步骤（Computational Steps），其行为不依赖于具体的实现方式或运行的硬件。
- **算法问题（Algorithmic Problem）** 由两个部分定义：
  - **实例集合（Set of Instances）**：算法可处理的输入数据范围。
  - **期望输出的性质（Desired Properties of Output）**。
- 评价一个算法的标准：
  - **正确性（Correctness）**
  - **时间效率（Efficiency in Time）**
  - **空间效率（Efficiency in Space）**

------

## **2. 代表性算法（Some Representative Algorithms）**

### **2.1 选择排序（Selection Sort）**

- **输入（Input）**：包含 n 个数的序列 A，以及一个空序列 B。

- **输出（Output）**：排序后的序列存储在 BB 中。

- **算法步骤（Steps）**：

  1. 在未排序部分找到最小值。
  2. 将该最小值放入排序序列的末尾。
  3. 在剩余未排序部分重复上述过程，直到所有元素排序完成。

- **时间复杂度（Time Complexity）**：

  - **最优情况（Best Case）**: O(n^2)
  - **最坏情况（Worst Case）**: O(n^2)
  - **平均情况（Average Case）**: O(n^2)
  - **特点**：不管输入情况如何，每次都需要遍历整个未排序数组，因此 **无论最佳、最差或平均情况，运行时间都为 O(n^2)**。

- **Python 实现**：

  ```python
  def selection_sort(array):
      for i in range(len(array)):
          min_idx = i
          for j in range(i + 1, len(array)):
              if array[j] < array[min_idx]:
                  min_idx = j
          array[i], array[min_idx] = array[min_idx], array[i]
      return array
  ```

### **2.2 搜索（Searching）**

- **输入**：一个包含 n 个元素的集合 A 和目标值 t。
- **输出**：返回目标值是否存在于集合中。

#### **线性搜索（Linear Search）**

- 逐个检查每个元素，直到找到目标值或遍历完整个集合。

- 时间复杂度

  ：

  - **最优情况**（Best Case）：O(1)（目标值在第一个位置）。
  - **最坏情况**（Worst Case）：O(n)（目标值在最后或不存在）。

#### **二分查找（Binary Search）**

- 适用于 **有序数组（Sorted Array）**。

- **算法思想**：

  1. 找到数组的中间元素。
  2. 如果中间元素是目标值，返回成功。
  3. 如果目标值小于中间元素，递归搜索左半部分，否则递归搜索右半部分。

- **时间复杂度**：

  - **最优情况（Best Case）**: O(1)
  - **最坏情况（Worst Case）**: O(log n)
  - **平均情况（Average Case）**: O(log n)

- **Python 实现**：

  ```python
  def binary_search(arr, target):
      left, right = 0, len(arr) - 1
      while left <= right:
          mid = left + (right - left) // 2
          if arr[mid] == target:
              return True
          elif arr[mid] < target:
              left = mid + 1
          else:
              right = mid - 1
      return False
  ```

------

## **3. 算法分析（Algorithm Analysis）**

### **3.1 主要分析内容**

- **正确性（Correctness）**
- **运行时间（Run Time）**
- **空间复杂度（Memory Usage）**Run Space

### **3.2 渐进分析（Asymptotic Analysis）**

- **大 O 记号（Big-O Notation）**: 上界，表示最坏情况的时间复杂度。
- **大 Ω 记号（Big-Omega Notation）**: 下界，表示最优情况的时间复杂度。
- **大 Θ 记号（Big-Theta Notation）**: 上下界相等，表示准确的时间复杂度。
- **示例**：
  - 3n^2−100n+6=O(n^2)
  - 3n^2−100n+6=Ω(n^2)
  - 3n^2−100n+6=Θ(n^2)

------

## **4. 代表性问题（Representative Problems）**

### **4.1 区间调度（Interval Scheduling）**

- **问题**：给定一组任务，每个任务有**起始时间（Start Time）**和 **结束时间（Finish Time）**，需要安排最大数量的互不冲突任务。
- **贪心算法（Greedy Algorithm）**：每次选择最早结束的任务，可以获得最优解。

### **4.2 加权区间调度（Weighted Interval Scheduling）**

- **问题**：类似于区间调度，但每个任务有一个权重（Weight），目标是**最大化权重总和**。
- **解决方案**：**动态规划（Dynamic Programming）**。

### **4.3 二分匹配（Bipartite Matching）**

- **问题**：给定两个集合（如**求职者和公司**、**医学生和医院**），找到最优匹配方案。
- **解决方案**：**网络流（Network Flow）** 方法。

### **4.4 独立集问题（Independent Set Problem）**

- **问题**：在图 G=(V,E)G=(V, E) 中，找到一个**最大的独立集（Independent Set）**，即其中任意两个节点都没有边相连。
- **应用**：社交网络中找互不冲突的好友组、任务调度等。
- **特点**：**NP 困难（NP-Hard）**，没有已知的高效算法。

### **4.5 竞争性设施选址（Competitive Facility Location）**

- **问题**：两家公司（如 Dunkin Donuts 和 Starbucks）竞争选择最佳店铺位置，同时满足**区域限制（Zoning Constraints）**。
- 建模方式：
  - 将每个位置视为**图（Graph）**中的**节点（Nodes）**。
  - 位置之间的冲突关系作为**边（Edges）**。
  - 目标是找到一个最优选址方案，使得收益最大化。

------

## **5. 结论（Summary）**

- **本次讲座重点介绍了算法的定义、几种经典的排序和搜索算法、渐进分析方法，以及多个具有代表性的问题及其解决方案**。
- **选择排序（Selection Sort）** 适用于小规模数据，时间复杂度较高。
- **二分搜索（Binary Search）** 是高效的搜索方法，但仅适用于**有序数据**。
- **渐进分析（Asymptotic Analysis）** 是分析算法复杂度的重要工具，帮助衡量算法性能。
- **实际问题（Real-World Problems）** 例如**区间调度、二分匹配、独立集**等问题，涉及不同算法设计方法，如**贪心算法、动态规划、网络流**。

------

这篇笔记总结了 **CS5800 Lecture 2** 的关键内容，适合作为学习和复习的参考资料。



以下是 **CS5800 Lecture 3** 的中文笔记，包含核心知识点，并且专业术语以英文标注：

------

# **CS5800 讲座 3 笔记**

## **1. 分治算法（Divide and Conquer Approach）**

### **1.1 什么是分治（What is Divide and Conquer）**

- **分治（Divide and Conquer）** 是一种递归（Recursion）策略，将问题分解为更小的子问题，分别求解，然后合并子问题的结果。
- 基本步骤：
  1. **分解（Divide）**：将问题拆分成多个子问题（通常是规模更小的相同问题）。
  2. **求解（Conquer）**：递归地解决每个子问题。
  3. **合并（Combine）**：将子问题的解合并为最终解。

------

## **2. 经典应用（Classic Applications）**

### **2.1 二分查找（Binary Search）**

- **问题**：在有序数组中查找一个目标值。
- **步骤**：
  1. 取数组的中间元素 A[mid]。
  2. 如果 A[mid] 等于目标值，返回成功。
  3. 如果 A[mid] 小于目标值，在右半部分继续查找；否则，在左半部分查找。
  4. 递归执行，直到找到目标值或范围为空。
- **时间复杂度**：O(log⁡n)

### **2.2 归并排序（Merge Sort）**

- **输入**：包含 n 个元素的数组。
- **输出**：排序后的数组。
- **算法步骤**：
  1. **分解**：将数组分成两半。
  2. **递归排序**：对每一半递归执行归并排序。
  3. **合并**：合并两个有序数组，使其仍然保持有序。
- **时间复杂度**：O(n log⁡n)

------

## **3. 递归关系（Recurrences）**

### **3.1 递归树（Recursion Trees）**

- 递归树是一种可视化递归调用的方法，用于分析算法的时间复杂度。
- 例子：归并排序的递归关系： T(n)=2T(n/2)+O(n)递归树展开后，高度为 log⁡n，每一层的计算量为 O(n)，因此总复杂度为： O(nlog⁡n)

------

## **4. 主定理（Master Theorem）**

### **4.1 递归方程的通解（Solving Recurrences）**

主定理用于求解形如：

T(n)=aT(n/b)+f(n)

的递归式，其中：

- a：子问题的个数。
- b：子问题规模的缩小因子。
- f(n)：合并子问题的额外计算量。

### **4.2 主定理的三种情况**

1. 如果 f(n)=O(n^(log⁡ba−ϵ))：

   - 递归部分占主导，解为：

   $$
   T(n) = \Theta(n^{\log_b a})
   $$

   

2. 如果 f(n)=Θ(n^(log⁡ba))：

   - 递归和合并部分相同，解为：

   $$
   T(n) = \Theta(n^{\log_b a} \log n)
   $$

3. 如果 
   $$
   f(n) = \Omega(n^{\log_b a + \epsilon})
   $$
   且满足正则性条件：

   - 合并部分占主导，解为：

   $$
   T(n) = \Theta(f(n))
   $$

   

### **4.3 归并排序的主定理分析**

- 归并排序的递归式：T(n) = 2T(n/2) + O(n)

  - a=2, b=2, f(n)=O(n)。

  - 计算 log_2 2 = 1

  - f(n)=O(n) 恰好等于
    $$
    n^{\log_2 2}
    $$
     ，属于第二种情况。

  - 因此，时间复杂度为： O(n log⁡n)

------

## **5. 递推替代法（Substitution Method）**

### **5.1 递推替代法的步骤**

1. 猜测解的形式。
2. 用数学归纳法（Mathematical Induction）证明猜测的解是正确的。
3. 适用于主定理无法直接求解的递归关系。

### **5.2 示例**

对于递归方程：

T(n)=3T(n/2)+O(n)T(n) = 3T(n/2) + O(n)

- 猜测解为 O(nlog⁡23)O(n^{\log_2 3})。
- 证明过程使用数学归纳法。

------

## **6. 数学归纳法（Mathematical Induction）**

### **6.1 归纳法基本步骤**

1. **基例（Base Case）**：验证最小规模的情况（如 n=1）。
2. **归纳假设（Inductive Hypothesis）**：假设对于 n 成立。
3. **归纳步（Inductive Step）**：证明对于 n+1 也成立。

### **6.2 强归纳法（Strong Induction）**

- 归纳假设不仅假设 P(n) 成立，还假设 P(1), P(2), ..., P(n) 都成立。

### **6.3 例子**

证明：

∑i=1ni=n(n+1)2\sum_{i=1}^{n} i = \frac{n(n+1)}{2}

- **基例**：n=1n=1，成立。
- **归纳假设**：假设对 nn 成立，即： ∑i=1ni=n(n+1)2\sum_{i=1}^{n} i = \frac{n(n+1)}{2}
- **归纳步**：对 n+1n+1： ∑i=1n+1i=∑i=1ni+(n+1)\sum_{i=1}^{n+1} i = \sum_{i=1}^{n} i + (n+1) 代入归纳假设： n(n+1)2+(n+1)=(n+1)(n+2)2\frac{n(n+1)}{2} + (n+1) = \frac{(n+1)(n+2)}{2} 证明成立。

------

## **7. 递归算法的正确性证明（Proving Correctness of Recursive Algorithms）**

### **7.1 证明递归算法正确性的步骤**

1. **基例**：验证最小输入规模时算法的正确性。
2. **归纳假设**：假设算法对 nn 规模的输入正确。
3. **归纳步**：证明对 n+1n+1 规模的输入仍然正确。

### **7.2 归并排序的正确性证明**

- **基例**：当数组长度为 1 时，已经是有序的。

- **归纳假设**：假设归并排序对大小为 nn 的数组正确。

- 归纳步

  ：

  1. 归并排序会将大小为 n+1n+1 的数组分为两个子数组。
  2. 根据归纳假设，两个子数组已正确排序。
  3. 合并两个有序数组仍然保持有序。
  4. 结论：归并排序对所有输入正确。

------

## **总结**

本次讲座重点介绍了：

- **分治算法（Divide and Conquer）** 及其应用（**二分查找、归并排序**）。
- **递归关系（Recurrences）** 及求解方法（**递归树、主定理**）。
- **递推替代法（Substitution Method）** 和 **数学归纳法（Mathematical Induction）**。
- **递归算法正确性证明（Proof of Recursive Algorithms）**，应用于 **归并排序（Merge Sort）**。

这为分析和设计高效算法提供了重要工具。