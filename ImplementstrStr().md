# Implement strStr()

Implement strStr().

Return the index of the first occurrence of needle in haystack, or -1 if needle is not part of haystack.

#### Example 1:

***Input***: haystack = "hello", needle = "ll"  
***Output***: 2
#### Example 2:

***Input***: haystack = "aaaaa", needle = "bba"  
***Output***: -1


code 

```php
<?php

function strStr1($haystack, $needle) {
    if (!$needle) return 0;
    $j = 0;
    $res = 0;
    $flag = 0;
    for ($i = 0; $i < strlen($haystack); $i++) {
        if ($haystack[$i] == $needle[$j]) {
            $flag = 1;
            if ($j == 0) $res = $i;
            $j++;
        }else if ($flag == 1){
            $i = $res;
            $j = 0;
            $flag = 0;
        }
        if ($j == strlen($needle)) {
            return $res;
        }
    }
    return -1;
}


```