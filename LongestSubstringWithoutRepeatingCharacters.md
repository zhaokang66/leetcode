# Longest Substring Without Repeating Characters
Given a string, find the length of the longest substring without repeating characters.

#### Example 1:

**Input**: "abcabcbb"  
**Output**: 3 
Explanation: The answer is "abc", with the length of 3. 
#### Example 2:

**Input**: "bbbbb"  
**Output**: 1
Explanation: The answer is "b", with the length of 1.
#### Example 3:
**Input**: "pwwkew"  
**Output**: 3  
**Explanation**: The answer is "wke", with the length of 3. 
             Note that the answer must be a substring, "pwke" is a subsequence and not a substring.
             
        
#### code
```php
<?php
class Solution {

    /**
     * @param String $s
     * @return Integer
     */
    function lengthOfLongestSubstring($s) {
        $start = 0;
        $map = [];
        $len = 0;
        if (!$s || strlen($s) == 0) {
            return 0;
        }
        for ($i=0;$i<strlen($s);$i++) {
            if (isset($map[$s[$i]]) && $start <= $map[$s[$i]]) {
                $start = $map[$s[$i]] + 1;
            }else {
                $len = max($len,$i-$start+1);
            }
            $map[$s[$i]] = $i;
        }
        return $len;
    }
}
$test = new Solution();
echo $test->lengthOfLongestSubstring("pwwkew");
```