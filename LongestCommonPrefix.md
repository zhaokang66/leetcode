# Longest Common Prefix
Write a function to find the longest common prefix string amongst an array of strings.

If there is no common prefix, return an empty string "".

#### Example 1:

***Input***: ["flower","flow","flight"]  
***Output***: "fl"  
#### Example 2: 

***Input***: ["dog","racecar","car"]  
***Output***: ""  
***Explanation***: There is no common prefix among the input strings.
code
```php
<?php

function longestCommonPrefix($strs) {
    if ($strs == [] || $strs[0] == [""] ) return "";
    if (count($strs) == 1) {
        return implode("",$strs);
    }
    $res = "";
    $len = 0;
    $i = 0;
    $j = 0;
    while ($strs[0][$j] == $strs[$i][$j] && isset($strs[0][$j])) {
        $i++;
        if ($i > count($strs) - 1) {
            $i = 0;
            $j++;
        }

    }
    return substr($strs[0],0,$j);
}

```