## Flatten 2D Vector
Design and implement an interator to flatten a 2D vector. It should support the following operations: **next** and **hasnext**

**Example** <br>
```cpp
vector2D iterator = new vector2D([[1,2], [3], [4]]);

iterator.next(); // return 1
iterator.next(); // return 2
iterator.next(); // return 3
iterator.hasNext(); return true
iterator.hasNext(); // return true
iterator.next(); //return 4
iterator.hasNext(); return true
```

**CODE**
```cpp
/* We have assumed that the classes have already been initialized */
class Solution{
    private:
    vector<int> flattenedVector;

    public:
    vector2D(vector<vector<int>> &v){
        flattenedVector.clear();
        for(auto& nums: v){
            flattenedVector.push_back(i);
        }
        reverse(flattenedVector.begin(), flattenedVector.end());
    }
    int next(){
        int res = flattenedvector.back();
        flattenedVector.pop_back();
        return res;
    }

    bool hasNext(){
        return !flattenedVector.empty();
    }
    


};

```
