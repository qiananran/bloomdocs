> STL（标准模板库）是C++的一个核心组成部分，提供了丰富的数据结构和算法，用于高效地处理各种数据和实现通用的编程模式。

![](https://photohosting.oss-cn-hangzhou.aliyuncs.com/notionCover/a4915e05a25549118b0ca44dfb28e429.jpg)

## 1、容器

### 1、序列容器（vector, list, deque等）

当谈到序列容器时，C++标准库提供了多种选择，每种都有其独特的特性和适用场景。以下是对常见序列容器的详细介绍，并包含一些示例说明它们的用法和特点。

### 1. **Vector**

- **特点**：
  - **连续存储**：所有元素在内存中连续存放，支持快速的随机访问。
  - **动态大小**：可以动态增长或收缩，通过分配更多的内存来实现。

- **例子**：
  ```cpp
  #include <vector>
  #include <iostream>
  
  int main() {
      std::vector<int> vec = {1, 2, 3};
      
      // 添加元素
      vec.push_back(4);
  
      // 遍历元素
      for (int i : vec) {
          std::cout << i << " ";
      }
      std::cout << std::endl;
  
      return 0;
  }
  ```

### 2. **List**

- **特点**：
  - **双向链表**：每个元素保存了指向前后元素的指针，支持快速的插入和删除操作，但不支持快速的随机访问。

- **例子**：
  ```cpp
  #include <list>
  #include <iostream>
  
  int main() {
      std::list<int> myList = {1, 2, 3};
  
      // 在头部插入元素
      myList.push_front(0);
  
      // 遍历元素
      for (int i : myList) {
          std::cout << i << " ";
      }
      std::cout << std::endl;
  
      return 0;
  }
  ```

### 3. **Deque**

- **特点**：
  - **双端队列**：支持在队头和队尾进行高效的插入和删除操作，比vector更适合频繁地在头部或中间插入/删除元素。

- **例子**：
  ```cpp
  #include <deque>
  #include <iostream>
  
  int main() {
      std::deque<int> myDeque = {1, 2, 3};
  
      // 在队头插入元素
      myDeque.push_front(0);
  
      // 遍历元素
      for (int i : myDeque) {
          std::cout << i << " ";
      }
      std::cout << std::endl;
  
      return 0;
  }
  ```

### 序列容器选择建议：

- **使用vector**：需要快速的随机访问和末尾插入/删除，且元素数量较大时。
- **使用list**：需要频繁的中间插入/删除操作，而不关心随机访问。
- **使用deque**：需要快速的头部或尾部插入/删除操作，但也需要随机访问，或者需要在中间位置进行插入/删除操作。

选择合适的序列容器能够根据需求最大化程序的效率和性能。

### 2、关联容器（map, set, multimap, multiset等）

关联容器在C++标准库中提供了基于键值对的数据存储和访问方式，主要包括`map`、`set`、`multimap`和`multiset`。它们与序列容器（如vector、list、deque）不同，主要用于实现高效的关联数据结构，支持快速的查找、插入和删除操作。以下是对这些关联容器的详细介绍和使用示例：

### 1. **Map**

- **特点**：
  - **键值对**：每个元素都是一个键值对，键是唯一的，用于快速查找值。
  - **自动排序**：按照键的顺序自动排序，默认按键的升序排列。

- **例子**：
  ```cpp
  #include <map>
  #include <iostream>
  
  int main() {
      std::map<std::string, int> myMap;
  
      // 插入键值对
      myMap["Alice"] = 25;
      myMap["Bob"] = 30;
      myMap["Eve"] = 22;
  
      // 访问元素
      std::cout << "Bob's age is " << myMap["Bob"] << std::endl;
  
      // 遍历所有键值对
      for (const auto& pair : myMap) {
          std::cout << pair.first << " is " << pair.second << " years old." << std::endl;
      }
  
      return 0;
  }
  ```

### 2. **Set**

- **特点**：
  - **唯一键集合**：所有元素都是唯一的，不能有重复的键。
  - **自动排序**：按照键的顺序自动排序，默认按升序排列。

- **例子**：
  ```cpp
  #include <set>
  #include <iostream>
  
  int main() {
      std::set<int> mySet = {5, 2, 8, 1, 6};
  
      // 插入元素
      mySet.insert(3);
      mySet.insert(5); // 重复元素不会被插入
  
      // 遍历元素
      for (int num : mySet) {
          std::cout << num << " ";
      }
      std::cout << std::endl;
  
      return 0;
  }
  ```

### 3. **Multimap**

- **特点**：
  - **允许重复键**：可以存储重复的键，键相同时会按照插入顺序保存。

- **例子**：
  ```cpp
  #include <map>
  #include <iostream>
  
  int main() {
      std::multimap<std::string, int> myMultimap;
  
      // 插入键值对
      myMultimap.insert({"Alice", 25});
      myMultimap.insert({"Bob", 30});
      myMultimap.insert({"Alice", 22}); // 允许重复键
  
      // 遍历所有键值对
      for (const auto& pair : myMultimap) {
          std::cout << pair.first << " is " << pair.second << " years old." << std::endl;
      }
  
      return 0;
  }
  ```

### 4. **Multiset**

- **特点**：
  - **允许重复元素**：可以存储重复的元素，元素相同时会按照插入顺序保存。

- **例子**：
  ```cpp
  #include <set>
  #include <iostream>
  
  int main() {
      std::multiset<int> myMultiset = {5, 2, 8, 1, 6};
  
      // 插入元素
      myMultiset.insert(5); // 允许重复元素
  
      // 遍历元素
      for (int num : myMultiset) {
          std::cout << num << " ";
      }
      std::cout << std::endl;
  
      return 0;
  }
  ```

### 关联容器选择建议：

- **使用map**：需要通过唯一键快速查找对应值的场景。
- **使用set**：需要存储唯一值并快速检查某个值是否存在的场景。
- **使用multimap**：需要存储允许重复键的键值对的场景。
- **使用multiset**：需要存储允许重复元素的集合的场景。

选择合适的关联容器能够根据需求最大化程序的效率和性能，尤其在需要频繁进行查找、插入和删除操作时尤为重要。

## 2、算法
### 1、基本算法（排序、查找、替换等）

基本算法在计算机科学中是基础中的基础，它们包括排序、查找、替换等常见操作，是许多更复杂算法和数据结构的基础。下面我会简要介绍这些基本算法的概念和常见实现方式：

### 1. **排序算法**

排序算法是将一组数据按照指定顺序重新排列的算法，常见的排序算法包括：

- **冒泡排序**（Bubble Sort）：通过相邻元素的比较和交换，每次将最大（或最小）的元素移动到末尾。
  
- **选择排序**（Selection Sort）：每次从未排序的部分选取最小（或最大）的元素，放到已排序部分的末尾。
  
- **插入排序**（Insertion Sort）：将未排序的元素逐个插入到已排序的部分的正确位置，类似打扑克牌时的排序。
  
- **快速排序**（Quick Sort）：通过一趟排序将待排序的数据分割成独立的两部分，递归地对两部分数据进行排序。
  
- **归并排序**（Merge Sort）：将数据分成两个已排序的部分，然后合并这两个部分以得到完全排序的数据。
  
- **堆排序**（Heap Sort）：利用堆这种数据结构来实现的一种排序算法，利用最大堆或最小堆的性质进行排序。

### 2. **查找算法**

查找算法是在数据集合中寻找特定元素的算法，常见的查找算法包括：

- **线性查找**（Linear Search）：从数据集合的起始位置开始，依次向后查找目标元素。
  
- **二分查找**（Binary Search）：前提是数据集合已排序，通过每次将搜索范围减半来查找目标元素。

### 3. **替换算法**

替换算法一般指字符串或数据处理中的操作，常见的包括：

- **字符串替换**：将字符串中的某个子串替换为另一个子串。
  
- **数组元素替换**：将数组中的某个特定元素替换为另一个元素。

### 示例代码：

下面是一些算法的简单示例代码（以C++为例）：

**冒泡排序示例：**
```cpp
#include <iostream>
#include <vector>

void bubbleSort(std::vector<int>& arr) {
    int n = arr.size();
    for (int i = 0; i < n - 1; ++i) {
        for (int j = 0; j < n - i - 1; ++j) {
            if (arr[j] > arr[j + 1]) {
                std::swap(arr[j], arr[j + 1]);
            }
        }
    }
}

int main() {
    std::vector<int> data = {64, 25, 12, 22, 11};
    bubbleSort(data);
    for (int num : data) {
        std::cout << num << " ";
    }
    std::cout << std::endl;
    return 0;
}
```

**二分查找示例：**
```cpp
#include <iostream>
#include <vector>

int binarySearch(std::vector<int>& arr, int target) {
    int left = 0, right = arr.size() - 1;
    while (left <= right) {
        int mid = left + (right - left) / 2;
        if (arr[mid] == target) {
            return mid; // 找到目标元素
        } else if (arr[mid] < target) {
            left = mid + 1; // 目标在右半部分
        } else {
            right = mid - 1; // 目标在左半部分
        }
    }
    return -1; // 没找到目标元素
}

int main() {
    std::vector<int> data = {11, 12, 22, 25, 64};
    int target = 25;
    int index = binarySearch(data, target);
    if (index != -1) {
        std::cout << "Found target at index " << index << std::endl;
    } else {
        std::cout << "Target not found" << std::endl;
    }
    return 0;
}
```

这些算法虽然简单，但在实际应用中起着基础作用，对理解和设计更复杂的算法和数据结构都至关重要。

### 2、泛型算法（for_each、transform、accumulate等）

泛型算法是一种利用模板实现的通用算法，它们独立于特定的数据类型，能够在不同类型的数据结构上工作。C++标准库中提供了许多有用的泛型算法，其中包括 `for_each`、`transform` 和 `accumulate` 等，它们分别用于不同的操作和数据处理需求。

### 1. `for_each` 算法

`for_each` 算法用于对容器中的每个元素执行特定的操作，其基本语法如下：

```cpp
template <class InputIterator, class Function>
Function for_each(InputIterator first, InputIterator last, Function fn);
```

- `first` 和 `last` 是迭代器，表示要操作的容器范围。
- `fn` 是一个函数对象（或函数指针），用来对每个元素执行的操作。

例如，对一个整数向量中的每个元素求平方并输出：

```cpp
#include <iostream>
#include <vector>
#include <algorithm>

void printSquare(int x) {
    std::cout << x * x << " ";
}

int main() {
    std::vector<int> vec = {1, 2, 3, 4, 5};
    std::for_each(vec.begin(), vec.end(), printSquare);
    std::cout << std::endl;
    return 0;
}
```

### 2. `transform` 算法

`transform` 算法用于对容器中的元素进行转换，并将结果存储到另一个容器中，其基本语法如下：

```cpp
template <class InputIterator, class OutputIterator, class UnaryOperation>
OutputIterator transform(InputIterator first1, InputIterator last1,
                         OutputIterator result, UnaryOperation op);
```

- `first1` 和 `last1` 定义了输入序列的范围。
- `result` 是输出序列的起始位置。
- `op` 是一个一元函数对象（或函数指针），用来对输入序列中的每个元素执行转换操作。

例如，将一个整数向量中的每个元素求平方并存储到另一个向量中：

```cpp
#include <iostream>
#include <vector>
#include <algorithm>

int square(int x) {
    return x * x;
}

int main() {
    std::vector<int> vec = {1, 2, 3, 4, 5};
    std::vector<int> result(vec.size());

    std::transform(vec.begin(), vec.end(), result.begin(), square);

    for (int x : result) {
        std::cout << x << " ";
    }
    std::cout << std::endl;
    return 0;
}
```

### 3. `accumulate` 算法

`accumulate` 算法用于对容器中的元素进行累积操作，其基本语法如下：

```cpp
template <class InputIterator, class T>
T accumulate(InputIterator first, InputIterator last, T init);
```

- `first` 和 `last` 定义了要累积的元素范围。
- `init` 是初始值，表示累积的起始点。

例如，计算一个整数向量中所有元素的总和：

```cpp
#include <iostream>
#include <vector>
#include <numeric>

int main() {
    std::vector<int> vec = {1, 2, 3, 4, 5};
    int sum = std::accumulate(vec.begin(), vec.end(), 0);
    std::cout << "Sum of vector elements: " << sum << std::endl;
    return 0;
}
```

这些泛型算法提供了高效且灵活的方式来处理容器中的数据，无需关心具体容器的类型，使得代码更加通用和易于重用。

## 3、迭代器
### 1、迭代器种类和特性

迭代器在C++中是一种抽象的概念，用于访问容器（比如数组、链表、集合等）中的元素，而不暴露容器的内部结构。C++标准库定义了多种迭代器类型，每种类型有不同的特性和使用场景。以下是常见的迭代器种类和它们的特性：

### 1. 输入迭代器 (Input Iterator)

- **特性**：
  - 只能单向移动，且只能通过递增操作 (`++`) 访问序列中的元素。
  - 支持比较运算符 (`==`, `!=`)，但不保证能够以通用方式进行算术运算。

- **应用**：
  - 适用于单遍扫描数据的情况，如读取输入流或者遍历一次容器。

### 2. 输出迭代器 (Output Iterator)

- **特性**：
  - 类似于输入迭代器，但只能进行单向递增操作，不支持比较运算符。

- **应用**：
  - 主要用于向容器中写入数据或者输出到输出流。

### 3. 前向迭代器 (Forward Iterator)

- **特性**：
  - 可以在单个方向上多次遍历容器，支持输入和输出操作。
  - 允许多次读取元素，但是每个元素只能被读取一次，因为一旦迭代器向前移动，之前的位置可能不再有效。

- **应用**：
  - 适用于需要多次遍历序列并可能在迭代过程中修改元素的情况。

### 4. 双向迭代器 (Bidirectional Iterator)

- **特性**：
  - 除了支持前向迭代器的操作外，还支持递减操作 (`--`)。
  - 允许向前和向后遍历容器。

- **应用**：
  - 适用于需要反向遍历容器的情况，比如双向链表。

### 5. 随机访问迭代器 (Random Access Iterator)

- **特性**：
  - 支持在常数时间内进行任意的移动（如 `+n`、`-n`）、比较（`<`, `>`, `<=`, `>=`）和间接访问（`[]`）操作。
  - 是最强大和最灵活的迭代器类型。

- **应用**：
  - 适用于需要随机访问容器中元素的情况，如数组。

### 迭代器的选择依赖于具体的需求和操作：

- 如果只需要顺序访问容器中的元素，并且只需单向遍历，输入迭代器足够。
- 如果需要反向遍历或者在遍历过程中修改元素，则需要使用双向迭代器。
- 如果需要通过索引或者进行复杂的跳跃式访问，随机访问迭代器是最佳选择。

C++标准库的算法和数据结构通常会根据迭代器的类型进行优化和选择，因此了解迭代器的种类和特性对于高效编程是非常重要的。

### 2、迭代器的高级应用

迭代器在C++中有许多高级应用，这些应用超出了基本的容器遍历和访问元素。以下是一些迭代器的高级应用场景和技巧：

### 1. 自定义容器的迭代器

C++允许开发者定义自己的容器类，并提供自定义的迭代器，以支持特定的数据结构和访问模式。这种自定义迭代器需要实现标准迭代器所需的一系列操作，如递增、递减、解引用等。

### 2. 迭代器适配器

迭代器适配器是一种设计模式，允许开发者将现有的迭代器接口转换为另一种接口或者增强迭代器的功能。常见的迭代器适配器包括 `std::reverse_iterator`（用于反向迭代）、`std::move_iterator`（用于移动语义）、`std::istream_iterator`（用于从输入流读取数据）等。

### 3. 插入迭代器

插入迭代器允许在容器中插入元素而无需关心元素的具体位置。常见的插入迭代器包括 `std::back_insert_iterator`（在容器末尾插入元素）、`std::front_insert_iterator`（在容器头部插入元素）、`std::insert_iterator`（在指定位置插入元素）等。

### 4. 迭代器和算法的结合使用

C++标准库提供了大量的算法（如排序、查找、变换等），这些算法通常以迭代器作为参数。通过结合不同类型的迭代器和算法，可以实现高效的数据处理和操作。例如，使用 `std::sort` 和随机访问迭代器可以快速对数组进行排序。

### 5. 多线程和迭代器

在多线程编程中，迭代器可以用于安全地并行遍历容器。C++11引入的 `std::iterator_traits` 和 `std::advance` 等工具，以及使用适当的同步机制（如互斥锁或原子操作），可以确保多线程环境下对容器的安全访问。

### 6. 迭代器的优化和性能考虑

了解不同类型迭代器的性能特征和适用场景，可以帮助优化代码的性能。例如，尽可能使用最高效的迭代器类型（如随机访问迭代器）以及适当选择算法（如二分查找替代线性查找），可以显著提升程序的执行效率。

总体来说，迭代器作为C++中强大的抽象工具，不仅限于简单的容器访问，还涉及到高级的设计模式、算法优化以及多线程并发等复杂领域，是C++程序员必须深入理解和熟练运用的重要概念之一。