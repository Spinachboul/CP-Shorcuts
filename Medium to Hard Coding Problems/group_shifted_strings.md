## Group Shifted Strings
Given a string, we can **shift** each of its letter to its successive letter, for
example: "abc" -> "bcd". We can keep "shifting" which forms the sequence:
"abc" -> "bcd" -> ... -> "xyz"
Given a list of strings which contains only lowercase alphabets, group all
strings that belong to the same shifting sequence.

**Example**
Input: ["abc", "bcd", "acef", "xyz", "az", "ba", "a", "z"],
Output:
[
["abc","bcd","xyz"],
["az","ba"],
["acef"],
["a","z"]
]

### Approach
The solution invloves hashing the strings based on their shifting sequence. Here is a step by step breakdown

1) **Hashing**
- The **hash** function converts each string into a unique hash value representing its shifting sequence
- We calculate an offset for each string by shifting all characters so that the first character becomes **a**.
- Finally, we compute a hash value using a **polynomial rolling hash** (https://www.geeksforgeeks.org/string-hashing-using-polynomial-rolling-hash-function/) method with a modulus to avoid overflow


### CODE

```cpp
class Solution{
    private:
    int hash(const string& s){
        long long h = 1;
        if(s.empty()) return h;
        int offset = s[0] - 'a';
        string ts;
        const int MOD = 1e9 + 7;
        for (auto& c: ts) ts += (c - 'a' - offset + 26) % 26 + 'a';
        for(auto& c: ts) h = (h * 31 + c - 'a') % MOD;
        return h;
    }
    public:
    vector<vector<string>> groupStrings (vector<string> &strings){
        unordered_map<int, vector<string>> shiftedStrings;
        for(auto& x: strings) shiftedStrings[hash(x)].push_back(x);
        vector<vector<string>> res;
        for(auto& m: shiftedStrings) res.push_back(m.second);

        return res;

    }
}
```

