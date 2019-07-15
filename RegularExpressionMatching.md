# Regular Expression Matching
Given an input string (s) and a pattern (p), implement regular expression matching with support for '.' and '*'.
```
'.' Matches any single character.
'*' Matches zero or more of the preceding element.
```
The matching should cover the entire input string (not partial).

#### Note:

* s could be empty and contains only lowercase letters a-z.  
* p could be empty and contains only lowercase letters a-z, and characters like . or *.  
#### Example 1:

***Input***:
s = "aa"  
p = "a"  
***Output***: false  
***Explanation***: "a" does not match the entire string "aa".  
#### Example 2:

***Input***:  
s = "aa"  
p = "a*"  
***Output***: true  
***Explanation***: '*' means zero or more of the precedeng element, 'a'. Therefore, by repeating 'a' once, it becomes "aa".  
#### Example 3:

***Input***:
s = "ab"  
p = ".*"  
***Output***: true  
***Explanation***: ".*" means "zero or more (*) of any character (.)".  
#### Example 4:

***Input***:
s = "aab"  
p = "c*a*b"  
***Output***: true  
***Explanation***: c can be repeated 0 times, a can be repeated 1 time. Therefore it matches "aab".  
#### Example 5:

***Input***:
s = "mississippi"  
p = "mis*is*p*."  
***Output***: false  
###### code
递归  
```php
<?php
function isMatch($s, $p) {
    $ns =  strlen($s);
    $np = strlen($p);
    if ($ns != 0 && $np == 0) {
        return false;
    }
    if ($ns == 0) {
        if ($np % 2 == 1) {
            return false;
        }
        $i = 1;
        while ($i < $np && $p[$i] == '*') {
            $i += 2;
        }
        if ($i == $np + 1) {
            return true;
        }else {
            return false;
        }
    }
    $match = $s[0] == $p[0] || $p[0] =='.';
    if ($np > 1 && $p[1] == '*') {
        return isMatch($s, substr($p, 2)) || ($match && isMatch(substr($s, 1),$p));
    }else {
        return $match && isMatch(substr($s, 1), substr($p, 1));
    }
}
```
动态规划
```php
<?PHP
function isMatch($s, $p) {
        $m = strlen($s);
        $n = strlen($p);
        $dp = array();
        $dp[0][0] = true;
//初始化第0行,除了[0][0]全为false，毋庸置疑，因为空串p只能匹配空串，其他都无能匹配
        for ($i = 1; $i <= $m; $i++)
            $dp[$i][0] = false;
//初始化第0列，只有X*能匹配空串，如果有*，它的真值一定和p[0][j-2]的相同（略过它之前的符号）
        for ($j = 1; $j <= $n; $j++)
            $dp[0][$j] = $j > 1 && '*' == $p[$j - 1] && $dp[0][$j - 2];

        for ($i = 1; $i <= $m; $i++)
        {
            for ($j = 1; $j <= $n; $j++)
            {
                if ($p[$j - 1] == '*')
                {
                    $dp[$i][$j] = $dp[$i][$j - 2] || ($s[$i - 1] == $p[$j - 2] || $p[$j - 2] == '.') && $dp[$i - 1][$j];

                }
                else   //只有当前字符完全匹配，才有资格传递dp[i-1][j-1] 真值
                {
                    $dp[$i][$j] = ($p[$j - 1] == '.' || $s[$i - 1] == $p[$j - 1]) && $dp[$i - 1][$j - 1];

                }
            }
        }
        return $dp[$m][$n];
}
```