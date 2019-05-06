# Palindrome Number
Determine whether an integer is a palindrome. An integer is a palindrome when it reads the same backward as forward.

#### Example 1:  

**Input**: 121  
**Output**: true  
#### Example 2:

**Input**: -121  
**Output**: false  
**Explanation**: From left to right, it reads -121. From right to left, it becomes 121-. Therefore it is not a palindrome.  
#### Example 3:  

**Input**: 10  
**Output**: false  
**Explanation**: Reads 01 from right to left. Therefore it is not a palindrome.  

#### code 
```php
<?php
class Solution {

    /**
     * @param Integer $x
     * @return Boolean
     */
    function isPalindrome($x) {
        $x = (string)$x;
        if (strlen($x == 1)) return true;
        $left = 0;
        $right = strlen($x) - 1;
        while ($left <= $right) {
            if ($x[$left] != $x[$right]) {
                return false;
            }
            $left++;
            $right--;
        }
        return true;
    }
}
$test = new Solution();
var_dump($test->isPalindrome(-121));
```