## Moore's Voting Algorithm

**Note It is used to calculate majority elements n/2**

**you can watch this video for dry run and intution - https://youtu.be/nP_ns3uSh80?si=McSFWPTIpt5wlPxv&t=460**

basically take first element and if you found it you do count++ and if otherelement appears count--;
if count = 0, current elem is the element

**code**
```cpp
class Solution {
public:
    int majorityElement(vector<int>& nums) {
        int count = 0;
        int element = 0;

        for(int i =0; i<nums.size(); i++){
            if(count == 0){
                element  = nums[i];
            }
            if(element == nums[i]){
                count++;
            }else{
                count--;
            }
        }
        return element;
    }
};
```

**time complexity** o(n)
