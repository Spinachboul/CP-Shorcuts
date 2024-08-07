## Meeting Rooms (Easy Version)
Given an array of meeting time intervals consisting of start and end times [[s1, e1], [s2, e2], [s3, e3],.....] (si < ei). Determine if a person could attend all the meetings

**Example** <br>

Input: [[0, 30], [5, 10], [15, 20]] <br>
Output: False <br>

**Approach**
You already know the logic, it is the previous element's ending time should always be smaller than the current element's starting time.

**CODE**
```cpp
class Solution{
    public:
    bool canAttendMeeting(vector<vector<int>> &intervals){
        if(intervals.empty()) return true;
        sort(intervals.begin() , intervals.end());
        for(int i=1 ; i<(int)intervals.size() ; i++){
            if(intervals[i-1][1] > intervals[i][0]){
                return false;

            }
        }
        return true;
    }
}

