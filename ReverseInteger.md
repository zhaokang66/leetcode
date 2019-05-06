# Reverse Integer
Given a 32-bit signed integer, reverse digits of an integer.

**Example 1**:

**Input**: 123  
**Output**: 321
  
**Example 2**:

**Input**: -123  
**Output**: -321
  
**Example 3**:

**Input**: 120  
**Output**: 21
  
**Note**:  
Assume we are dealing with an environment which could only store integers within the 32-bit signed integer range: [−231,  231 − 1]. For the purpose of this problem, assume that your function returns 0 when the reversed integer overflows.

#### code
```php
<?php
class Solution {

    /**
     * @param Integer $x
     * @return Integer
     */
    function reverse($x) {
        $res = 0;
        $temp = $x;
        while (intval($x) != 0) {
            $i = $x % 10;
            $res = $res * 10 + $i;
            $x = $x / 10;
        }
        if ($res < (-2147483648) || $res > 2147483647)
            return 0;
        return $res;
    }
}
$test = new Solution();
var_dump($test->reverse(-123));
```