## Vector

1. How to declare a vector?

```c++
#include <iostream>
#include <vector>

int main()
{
    std::vector <int> data = {1, 2, 3};

    return 0;
}
```

Certain functions associated with the vectors are:

1. Element access:
   - `front()`
   - `back()`
2. Capacity:
   - `size()`
   - `empty()`
3. Iterator:
   - `begin()`
   - `end()`
   - `rbegin()`
   - `rend()`
4. Modifiers:
   - `push_back()`
   - `pop_back()`
   - `emplace_back()`
   - `clear()`
   - `erase()`

More info: 👉 [geeksforgeeks](https://www.geeksforgeeks.org/vector-in-cpp-stl/)

2. Some operations:

```c++
#include <iostream>
#include <vector>

#define f(i, a, b) for(int i = a; i < b; i++)
#define F(i, a, b) for(int i = a; i <= b; i++)

int main()
{
    std::vector <int> data = {1, 2, 3};
    data.push_back(4);

    F(i, 0, data.size()-1) {
        std::cout << data[i];
    }

    std::cout << data.front() << " " << data.back();

    return 0;
}
```

---

3. Passing vector to function

```c++
#include <iostream>
#include <vector>

#define f(i, a, b) for(int i = a; i < b; i++)
#define F(i, a, b) for(int i = a; i <= b; i++)

void printVector(std::vector <int> data) {
    F(i, 0, data.size()-1) {
        std::cout << data[i] << "\t";
    }
}

int main()
{
    std::vector <int> data = {1, 2, 3};
    printVector(data);

    return 0;
}
```

4. Range based for loop

```c++
#include <iostream>
#include <vector>

int main()
{
    std::vector <int> vec = {1, 2, 3};

    for(int n: vec) {
        std::cout << n << " ";
    }

    /*
    for(int i = 0; i < vec.size(); i++) {
        std::cout << vec[i] << " ";
    }
    */

    return 0;
}

```
