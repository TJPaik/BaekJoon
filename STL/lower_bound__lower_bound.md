# Upper bound / Lower bound
* https://cplusplus.com/reference/algorithm/upper_bound/
* On average, logarithmic in the distance between first and last: Performs approximately $log_2(N)+1$ element comparisons (where $N$ is this distance).

## Example 1
```cpp
// tested on c++20
#include <bits/stdc++.h>

using namespace std;

int main() {
    map<int, int> mp;

    mp.insert({10, 100});
    mp.insert({20, 500});
    cout << "Keys : 10, 20" << endl;
    cout << endl;

    vector<int> test_n{0, 10, 15, 20, 30};
    map<int, int>::iterator iter;

    cout << "lower_bound test" << endl;
    cout << "\tN\t*iter " << endl;
    for (auto el: test_n) {
        cout << "\t" << el << ":";
        iter = mp.lower_bound(el);
        cout << "\t" << (*iter).first;
        if (iter == mp.begin())
            cout << "\tbegin";
        if (iter == mp.end())
            cout << "\tend";
        cout << endl;
    }

    cout << "upper_bound test" << endl;
    cout << "\tN\t*iter " << endl;
    for (auto el: test_n) {
        cout << "\t" << el << ":";
        iter = mp.upper_bound(el);
        cout << "\t" << (*iter).first;
        if (iter == mp.begin())
            cout << "\tbegin";
        if (iter == mp.end())
            cout << "\tend";
        cout << endl;
    }
    return 0;
}
```
## output 1
```
Keys : 10, 20

lower_bound test
	N	*iter 
	0:	10	begin
	10:	10	begin
	15:	20
	20:	20
	30:	2	end
upper_bound test
	N	*iter 
	0:	10	begin
	10:	20
	15:	20
	20:	2	end
	30:	2	end
```

## Example 2

```cpp
// tested on c++20
#include <iostream>     // std::cout
#include <algorithm>    // std::lower_bound, std::upper_bound, std::sort
#include <vector>       // std::vector

int main () {
  int myints[] = {10,20,30,30,20,10,10,20};
  std::vector<int> v(myints,myints+8);           // 10 20 30 30 20 10 10 20

  std::sort (v.begin(), v.end());                // 10 10 10 20 20 20 30 30

  std::vector<int>::iterator low,up;
  low=std::lower_bound (v.begin(), v.end(), 20); //          ^
  up= std::upper_bound (v.begin(), v.end(), 20); //                   ^

  std::cout << "lower_bound at position " << (low- v.begin()) << '\n';
  std::cout << "upper_bound at position " << (up - v.begin()) << '\n';

  return 0;
}
```
## output 2
```
lower_bound at position 3
upper_bound at position 6
```