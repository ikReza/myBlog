Basic code to check if a number is prime or not

`Brute Force` approcah

```c++
#include <iostream>

bool isPrime(int num) {
    if(num < 2) return false;

    for(int i = 2; i < num; i++) {
        if(num % i == 0) return false;
    }

    return true;
}

int main()
{
    int num;
    std::cin >> num;
    auto result = isPrime(num);

    result ? std::cout << "Prime" : std::cout << "Not Prime";

    return 0;
}
```

`Time complexity` of this code is `O(n)`.

Let's assume the input is 31. So we need to check (31-2) times to find out if this number is divisible or not. So time complexity is `O(n-2)`. Ignoring the constant value, final time complexity: `O(n)`.

---

Let's find out how can we reduce this time complexity.

```c++
#include <iostream>
#include <cmath>

bool isPrime(int num) {
    if(num < 2) return false;

    for(int i = 2; i <= sqrt(num); i++) {
        if(num % i == 0) return false;
    }

    return true;
}
```

`Time complexity` of this code is `O(√n)`.

Let's assume our number is 39. So square root of 39 is 6.25 ~ 6. 39 has 2 divisors except 1 - 3 and 13. Here we can see that, 3 is < 6 and 13 is > 6. This is true for every number. So we can check only `√n` number of times. By doing this we can reduce the time complexity.

But `sqrt(num)` will return floating number sometimes. To avoid that we can change our code slightly:

```c++
#include <iostream>

bool isPrime(int num) {
    if(num < 2) return false;

    for(int i = 2; i*i <= num; i++) {
        if(num % i == 0) return false;
    }

    return true;
}
```

> Problem - 1: Print out all the prime numbers upto n(which will be given).

```c++
#include <iostream>
#include <vector>

bool isPrime(int num) {
    if(num < 2) return false;

    for(int i = 2; i*i <= num; i++) {
        if(num % i == 0) return false;
    }

    return true;
}

std::vector <int> getPrimes(int n) {
    std::vector <int> primes;

    for(int i = 2; i <= n; i++) {
        if(isPrime(i)) {
            primes.emplace_back(i);
        }
    }

    return primes;
}

int main()
{
    int num;
    std::cin >> num;
    auto result = getPrimes(num);
    // std::vector <int> result = getPrimes(num);

    for(int i = 0; i < result.size(); i++) {
        std::cout << result[i] << " ";
    }
    /*
    for(int prime: result){
        std::cout << prime << " ";
    }
    */

    return 0;
}
```

`Time complexity` of this code is `O(n√n)`.

---

### Sieve of Eratosthenes

```c++
#include <iostream>

#define MAX 1000001
bool primes[MAX]; // all values will be 0 means false. We're considering false means prime number

void sieve(int num) {

    // 0 and 1 is not a prime number. So marking them 1 means true means not prime
    primes[0] = primes[1] = 1;

    // all multiples of 2 will be composite number
    for(int i = 4; i <= num; i += 2) {
        primes[i] = 1;
    }

    for(int i = 3; i*i <= num; i += 2) {
        if(primes[i] == 0) {
            for(int j = 3*i; j <= num; j += 2*i) {
                primes[j] = 1;
            }
        }
    }
}

int main()
{
    int num;
    std::cin >> num;
    sieve(num);

    primes[num] ? std::cout << "Not Prime" : std::cout << "Prime";

    return 0;
}
```

`O(n(log(n))(log(log(n))))`

> Print all the prime number upto n

```c++
#include <iostream>
#include <vector>

using namespace std;

bool primes[100001];

void sieve(int n) {
    primes[0] = primes[1] = 1;
    for(int i = 4; i <= n; i += 2) {
        primes[i] = 1;
    }

    for(int i = 3; i*i <= n; i += 2) {
        if(!primes[i]) {
            for(int j = 3*i; j <= n; j += 2*i) {
                primes[j] = 1;
            }
        }
    }
}

vector<int> getPrimes(int n) {
    vector <int> vec;
    sieve(n);
    for(int i = 2; i <= n; i++) {
        if(!primes[i]) {
            vec.emplace_back(i);
        }
    }

    return vec;
}

int main()
{
    int n;
    cin >> n;

    auto result = getPrimes(n);

    for(int prime: result){
        cout << prime << " ";
    }
}

```

> **Prime factorization upto n**

```c++
#include <iostream>
#include <vector>

using namespace std;

vector<int> primeFactors(int n) {
    vector<int> vec;

    while(n % 2 == 0) {
        vec.emplace_back(2);
        n /= 2;
    }

    for(int i = 3; i*i <= n; i += 2) {
        while(n % i == 0) {
            vec.emplace_back(i);
            n /= i;
        }
    }

    if(n > 2) vec.emplace_back(n);

    return vec;
}

int main()
{
    int n;
    cin >> n;

    auto result = primeFactors(n);
    for(int elem: result) {
        cout << elem << " ";
    }
}
```

`Space complexity` can be reduced without declaring vector. We directly print out(`cout`) the value instead of using `emplace_back(x)`
