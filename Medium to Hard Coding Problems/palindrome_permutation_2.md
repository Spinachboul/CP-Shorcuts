## Palindrome Permutation 2
Given a string s, return all the palindromic permutations (without duplicates) of it. Return an empty list if no palindromic permutation could be form

**Example** <br>
Input: "aabb" <br>
Output: ["aaba", "baab"] <br>

**CODE**
```cpp
class Solution{
    private:
    bool isPalindrome(string& s){
        int numOfOdds = 0;
        for(auto& c: s) ++cnt[s];
        for(auto& [k, v]: cnt){
            if(v%2==1)
                if(++numOfOdds > 1)
                    return false;
        }
        return true;
    }
    public:
    unordered_map<char, int> cnt;
    vector<string> generatePalindromes(string s){
        if(!isPalindrmic(s)) return {};
        unordered_set<string> permutation;
        string prefix, oddchar;
        for(auto& [k, v]: cnt){
            prefix += string(v/2, k);
            if(v%2==1) oddchar = string(1, k);
        }
        sort(prefix.begin(), prefix.end());
        do{
            string suffix(prefix);
            reverse(suffix.begin() , suffix.end());
            permutation.insert(prefix + oddchar + suffix);

        }while (next_permutation(prefix.begin() , prefix.end()));
        return vector<string> (permutation.begin() , permutation.end());
    }

};
```