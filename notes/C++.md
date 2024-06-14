##  iterator` 和 `const_iterator

在C++标准模板库（STL）中，`iterator` 和 `const_iterator` 是用于遍历容器（如`vector`、`list`、`map`等）的对象。它们提供了一种统一的方式来访问容器中的元素，无论容器的底层实现细节如何。下面是对`iterator`和`const_iterator`的详细解释。

### `iterator`

`iterator` 是一种对象，它指向容器中的某个元素，并允许对该元素进行读取和修改。`iterator` 类似于指针，但比指针更灵活，因为它可以用来遍历STL容器。通过`iterator`，可以实现对容器元素的遍历、访问和修改。

#### 特性：

- 可以指向容器中的任意元素。
- **支持递增（`++`）和递减（`--`）操作来遍历容器。**
- 允许修改所指向的元素。
- **支持解引用操作符（`*`）来访问所指向的元素。**

#### 示例代码：

*for* (std::vector<int>::iterator it = vec.begin(); it != vec.end(); ++it) {*
        **it *= 2;  // 将每个元素乘以 2*
    }*

```
cpp复制代码#include <iostream>
#include <vector>

int main() {
    std::vector<int> vec = {1, 2, 3, 4, 5};

    // 使用 iterator 遍历并修改元素
    for (std::vector<int>::iterator it = vec.begin(); it != vec.end(); ++it) {
        *it *= 2;  // 将每个元素乘以 2
    }

    // 输出修改后的元素
    for (std::vector<int>::iterator it = vec.begin(); it != vec.end(); ++it) {
        std::cout << *it << " ";
    }
    std::cout << std::endl;

    return 0;
}
```

### `const_iterator`

`const_iterator` 是一种只读的迭代器，它指向容器中的某个元素，但不允许修改该元素。使用`const_iterator`可以保证遍历容器时不修改其内容，适用于需要只读访问的场景。

#### 特性：

- 可以指向容器中的任意元素。
- 支持递增（`++`）和递减（`--`）操作来遍历容器。
- 不允许修改所指向的元素。
- 支持解引用操作符（`*`）来访问所指向的元素，但不能通过它修改元素。

#### 示例代码：

```
cpp复制代码#include <iostream>
#include <vector>

int main() {
    std::vector<int> vec = {1, 2, 3, 4, 5};

    // 使用 const_iterator 遍历元素
    for (std::vector<int>::const_iterator it = vec.cbegin(); it != vec.cend(); ++it) {
        std::cout << *it << " ";  // 只读访问元素
    }
    std::cout << std::endl;

    return 0;
}
```

### `iterator` 和 `const_iterator` 的比较

1. **修改权限**：
   - `iterator`：可以修改所指向的元素。
   - `const_iterator`：不能修改所指向的元素，只能进行只读访问。
2. **用途**：
   - `iterator`：适用于需要遍历并可能修改容器中元素的场景。
   - `const_iterator`：适用于只需要遍历和读取容器中元素，不允许修改的场景。
3. **定义和使用**：
   - `iterator`：通过 `container_type::iterator` 定义，如 `std::vector<int>::iterator`。
   - `const_iterator`：通过 `container_type::const_iterator` 定义，如 `std::vector<int>::const_iterator`。

### 示例：在函数中使用迭代器

下面是一个示例，展示如何在函数中使用 `iterator` 和 `const_iterator`：

```
cpp复制代码#include <iostream>
#include <vector>

// 使用 iterator 的函数，允许修改元素
void doubleElements(std::vector<int>& vec) {
    for (std::vector<int>::iterator it = vec.begin(); it != vec.end(); ++it) {
        *it *= 2;
    }
}

// 使用 const_iterator 的函数，只读访问元素
void printElements(const std::vector<int>& vec) {
    for (std::vector<int>::const_iterator it = vec.cbegin(); it != vec.cend(); ++it) {
        std::cout << *it << " ";
    }
    std::cout << std::endl;
}

int main() {
    std::vector<int> vec = {1, 2, 3, 4, 5};

    // 修改元素
    doubleElements(vec);

    // 输出修改后的元素
    printElements(vec);

    return 0;
}
```

通过使用 `iterator` 和 `const_iterator`，可以根据具体需求选择合适的迭代器类型，以便在遍历容器时保证代码的安全性和可读性。

## 深拷贝和浅拷贝

```C++
浅拷贝（默认构造）
#include <iostream>

class ShallowCopy {
public:
    int* data;

    // 构造函数
    ShallowCopy(int value) {
        data = new int(value);
        std::cout << "Constructor called. Value: " << *data << std::endl;
    }

    // 析构函数
    ~ShallowCopy() {
        delete data;
        std::cout << "Destructor called." << std::endl;
    }
};

int main() {
    ShallowCopy obj1(10);
    ShallowCopy obj2 = obj1;  // 调用默认的浅拷贝构造函数

    std::cout << "obj1's data: " << *obj1.data << std::endl;
    std::cout << "obj2's data: " << *obj2.data << std::endl;

    *obj1.data = 20;  // 修改 obj1 的数据
    std::cout << "After modifying obj1's data:" << std::endl;
    std::cout << "obj1's data: " << *obj1.data << std::endl;
    std::cout << "obj2's data: " << *obj2.data << std::endl;

    return 0;
}

```

```C++
#include <iostream>

class DeepCopy {
public:
    int* data;

    // 构造函数
    DeepCopy(int value) {
        data = new int(value);
        std::cout << "Constructor called. Value: " << *data << std::endl;
    }

    // 拷贝构造函数（深拷贝）
    DeepCopy(const DeepCopy& other) {
        data = new int(*other.data);
        std::cout << "Copy constructor called. Value: " << *data << std::endl;
    }

    // 拷贝赋值运算符（深拷贝）
    DeepCopy& operator=(const DeepCopy& other) {
        if (this != &other) {
            delete data;  // 释放已有资源
            data = new int(*other.data);
            std::cout << "Copy assignment operator called. Value: " << *data << std::endl;
        }
        return *this;
    }

    // 析构函数
    ~DeepCopy() {
        delete data;
        std::cout << "Destructor called." << std::endl;
    }
};

int main() {
    DeepCopy obj1(10);
    DeepCopy obj2 = obj1;  // 调用深拷贝构造函数

    std::cout << "obj1's data: " << *obj1.data << std::endl;
    std::cout << "obj2's data: " << *obj2.data << std::endl;

    *obj1.data = 20;  // 修改 obj1 的数据
    std::cout << "After modifying obj1's data:" << std::endl;
    std::cout << "obj1's data: " << *obj1.data << std::endl;
    std::cout << "obj2's data: " << *obj2.data << std::endl;

    return 0;
}

```

## 互斥锁和条件变量

## 作用域解析运算符 `::`

`::` 运算符用于访问类的静态成员、全局变量和函数，以及命名空间中的成员。

## 成员访问运算符 `.`

`.` 运算符用于访问对象的成员变量和成员函数。当你有一个对象实例时，可以使用 `.` 运算符来访问该对象的成员。

## 指针成员访问运算符 `->`

`->` 运算符用于通过指针访问对象的成员变量和成员函数。当你有一个指向对象的指针时，可以使用 `->` 运算符来访问该对象的成员。

## operator

关键字，用于重载或者定义操作符

## Lambda表达式

Lambda表达式是C++11引入的一个非常方便的特性，它允许你定义匿名函数，即没有名称的函数对象。Lambda表达式可以在需要函数对象的地方 inline 地编写函数逻辑，这使得代码更加简洁和直观。

Lambda表达式的基本语法如下：

```
[捕获列表](参数列表) mutable -> 返回类型 {
    // 函数体
}
```

其中：

- **捕获列表**：指定了在Lambda表达式外部作用域中哪些变量可以被捕获进来使用，以及是以值还是引用的方式捕获。捕获列表可以是空白的，也可以包含多个条目，例如`[=]`表示以值的方式捕获所有外部变量，`[&]`表示以引用的方式捕获所有外部变量，`[a, &b]`表示以值的方式捕获变量`a`，以引用的方式捕获变量`b`。
- **参数列表**：与普通函数的参数列表类似，指定了Lambda表达式可以接受的外部参数。如果Lambda表达式不接受任何参数，可以省略参数列表或者使用`()`。
- **mutable**：这是一个可选的修饰符，如果使用了它，则允许在Lambda表达式中修改以值方式捕获的外部变量。
- **返回类型**：指定了Lambda表达式的返回类型。如果Lambda表达式的函数体只包含单一的返回语句，或者返回类型可以自动推导，则可以省略返回类型，让编译器自动推导。
- **函数体**：包含了Lambda表达式的实际代码。

下面是一个简单的Lambda表达式示例：

cpp

复制

```
std::vector<int> nums = {1, 2, 3, 4, 5};
int sum = 0;
std::for_each(nums.begin(), nums.end(), [&](int n) {
    sum += n;
});
std::cout << "Sum: " << sum << std::endl;
```

在这个例子中，`std::for_each`算法接受一个Lambda表达式作为第三个参数，该Lambda表达式以引用的方式捕获了外部变量`sum`，并接受一个整数参数`n`。Lambda表达式的目的是将`n`累加到`sum`变量中。

Lambda表达式在STL算法中使用非常广泛，可以极大地简化代码，并提高代码的可读性。它们也可以用于需要函数对象的地方，如排序、过滤、映射等操作。

## io多路复用

## 多线程

## TCP三次握手

## TCP断连四次挥手

## 事件驱动编程

事件驱动编程模型依赖于事件和回调函数。在这种模型中，程序响应用户操作或系统事件，而不是按照代码的顺序执行。当事件发生时，程序会调用相应的回调函数来处理该事件。事件驱动编程通常用于用户界面和图形界面应用程序，以及网络编程中，特别是在处理大量的并发连接时。

关键特点：

- **异步操作**：事件发生时，相关的代码会被异步执行，不会阻塞主线程。
- **事件循环**：程序通常有一个主事件循环，用于监听和分派事件。
- **回调函数**：事件的处理通常通过回调函数来完成。
- **资源效率**：可以高效地处理大量的并发操作，而不需要为每个操作创建单独的线程或进程。

## 线程并发模型

### 线程并发

线程并发模型涉及在多个线程中分配和执行任务。在这种模型中，多个线程可以同时运行，每个线程执行特定的任务。线程可以由操作系统调度，并在多核处理器上并行执行，从而提高应用程序的吞吐量和响应能力。

关键特点：

- **并行执行**：多个线程可以同时执行，从而利用多核处理器的并行性。
- **同步和通信**：线程之间可能需要同步和通信，以协调共享资源和数据。
- **资源开销**：每个线程都有自己的栈空间和上下文，因此创建大量的线程可能会消耗大量的资源。
- **编程复杂度**：线程同步和死锁问题可能会增加程序的复杂性。

对比

- **资源使用**：事件驱动通常使用较少的线程资源，因为它依赖于单线程事件循环和异步回调。线程并发可能会使用更多的线程资源，尤其是在多核处理器上。
- **并发处理能力**：事件驱动适合处理大量的并发I/O操作，而线程并发适合处理计算密集型任务，尤其是在多核处理器上。
- **编程模型**：事件驱动编程通常需要开发者理解异步编程和事件分派机制。线程并发则更接近传统的顺序编程模型，但需要处理线程同步和通信。

explicit

## 异步 同步