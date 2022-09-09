# Problem #1996 ([The Number of Weak Characters in the Game](https://leetcode.com/problems/the-number-of-weak-characters-in-the-game/) | Array, Greedy, Monotonic Stack, Sorting, Stack)

You are playing a game that contains multiple characters, and each of the characters has **two** main properties: **attack** and **defense**. You are given a 2D integer array `properties` where `properties[i] = [attackᵢ, defenseⱼ]` represents the properties of the `iᵗʰ` character in the game.

A character is said to be **weak** if any other character has **both** attack and defense levels **strictly greater** than this character's attack and defense levels. More formally, a character `i` is said to be **weak** if there exists another character `j` where `attackⱼ > attackᵢ` and `defenseⱼ > defenseᵢ`.

*Return the number of **weak** characters.*

## Example 1

### Input: 

    properties = [[5,5],[6,3],[3,6]]

### Output: 

    0

### Explanation: 

    No character has strictly greater attack and defense than the other.

# Solutions

## Sorting

### Codes

- **Java**
<br/>

- **C++**
```cpp
class Solution {
public:
    static bool comp(vector<int>& a, vector<int>& b){
        if(a[0] == b[0])
            return a[1] < b[1];
        return a[0] > b[0];
    }
    
    int numberOfWeakCharacters(vector<vector<int>>& properties) {
        int n = properties.size();
        int count = 0;
        sort(properties.begin(), properties.end(), comp);
        int maxN = INT_MIN;
        for(int i = 0; i < n; i++){
            if(properties[i][1] < maxN)
                count++;
            maxN = max(maxN, properties[i][1]);
        }
        return count;
    }
};
```
![image](https://user-images.githubusercontent.com/89616705/189256594-878bbd1c-cee3-4386-ae0d-7ab9a206d4a4.png)
<br/>