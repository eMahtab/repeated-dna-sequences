# Repeated DNA Sequences
## https://leetcode.com/problems/repeated-dna-sequences

The DNA sequence is composed of a series of nucleotides abbreviated as 'A', 'C', 'G', and 'T'.

For example, "ACGAATTCCG" is a DNA sequence.
When studying DNA, it is useful to identify repeated sequences within the DNA.

Given a string s that represents a DNA sequence, return all the 10-letter-long sequences (substrings) that occur more than once in a DNA molecule. You may return the answer in any order.

```java
Example 1:

Input: s = "AAAAACCCCCAAAAACCCCCCAAAAAGGGTTT"
Output: ["AAAAACCCCC","CCCCCAAAAA"]

Example 2:

Input: s = "AAAAAAAAAAAAA"
Output: ["AAAAAAAAAA"]
``` 

### Constraints:

1. 1 <= s.length <= 105
2. s[i] is either 'A', 'C', 'G', or 'T'.

## Implementation
```java
class Solution {
    public List<String> findRepeatedDnaSequences(String s) {
        List<String> result = new ArrayList<>();
        if(s.length() <= 10)
          return result;
        Map<String,Integer> map = new HashMap<>();  
        for(int i = 0; i <= s.length() - 10; i++) {
            String substr = s.substring(i, i+10);
            int occurrence = map.getOrDefault(substr, 0);
            map.put(substr, occurrence + 1); 
        }
        for(String str : map.keySet()) {
            if(map.get(str) > 1)
             result.add(str);
        }
        return result;  
    }
}
```
