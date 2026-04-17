# ✅ Bubble Sort

```cpp
#include <bits/stdc++.h>
using namespace std;

vector<int> bubbleSort(vector<int> arr) {
    int n = arr.size();

    for (int i = 0; i < n - 1; i++) {
        for (int j = 0; j < n - i - 1; j++) {
            if (arr[j] > arr[j + 1]) {
                swap(arr[j], arr[j + 1]);
            }
        }
    }

    return arr;
}

int main() {
    vector<int> a = {8, 3, 5, 1, 9, 6};

    vector<int> sorted = bubbleSort(a);

    for (int x : sorted)
        cout << x << " ";
}
```


# ✅ Full Code (Easy Visual Merge Sort)

```cpp
#include <bits/stdc++.h>
using namespace std;

// Two sorted arrays merge than array return 
vector<int> mergeTwo(vector<int> left, vector<int> right) {
    vector<int> result;

    int i = 0, j = 0;

    while (i < left.size() && j < right.size()) {
        if (left[i] < right[j]) {
            result.push_back(left[i]);
            i++;
        } else {
            result.push_back(right[j]);
            j++;
        }
    }

    while (i < left.size()) {
        result.push_back(left[i]);
        i++;
    }

    while (j < right.size()) {
        result.push_back(right[j]);
        j++;
    }

    return result;
}

// Merge Sort function (call by value + return)
vector<int> mergeSort(vector<int> arr) {
    if (arr.size() <= 1)
        return arr;

    int mid = arr.size() / 2;

    vector<int> left(arr.begin(), arr.begin() + mid);
    vector<int> right(arr.begin() + mid, arr.end());

    vector<int> sortedLeft = mergeSort(left);
    vector<int> sortedRight = mergeSort(right);

    return mergeTwo(sortedLeft, sortedRight);
}

int main() {
    vector<int> a = {8, 3, 5, 1, 9, 6};

    vector<int> sorted = mergeSort(a);

    for (int x : sorted) {
        cout << x << " ";
    }

    return 0;
}
```

