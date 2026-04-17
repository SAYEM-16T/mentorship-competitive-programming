# ✅ Linear Search Code (Simple)

```cpp id="2m1x7s"
#include <bits/stdc++.h>
using namespace std;

int linearSearch(vector<int> arr, int target) {
    for (int i = 0; i < arr.size(); i++) {
        if (arr[i] == target) {
            return i; // index return করবে
        }
    }
    return -1; // না পেলে
}

int main() {
    vector<int> a = {8, 3, 5, 1, 9, 6};
    int target = 5;

    int index = linearSearch(a, target);

    if (index != -1)
        cout << "Found at index: " << index;
    else
        cout << "Not Found";
}
```



# ✅ Binary Search Code (Simple, Iterative)

```cpp id="y5g7kx"
#include <bits/stdc++.h>
using namespace std;

int binarySearch(vector<int> arr, int target) {
    int left = 0;
    int right = arr.size() - 1;

    while (left <= right) {
        int mid = (left + right) / 2;

        if (arr[mid] == target)
            return mid;
        else if (arr[mid] < target)
            left = mid + 1;
        else
            right = mid - 1;
    }

    return -1;
}

int main() {
    vector<int> a = {1, 3, 5, 6, 8, 9}; // sorted array
    int target = 5;

    int index = binarySearch(a, target);

    if (index != -1)
        cout << "Found at index: " << index;
    else
        cout << "Not Found";
}
```
