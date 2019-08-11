#  Integer to Roman
Roman numerals are represented by seven different symbols: I, V, X, L, C, D and M.  
```
Symbol       Value
I             1
V             5
X             10
L             50
C             100
D             500
M             1000
```
For example, two is written as II in Roman numeral, just two one's added together. Twelve is written as, XII, which is simply X + II. The number twenty seven is written as XXVII, which is XX + V + II.  

Roman numerals are usually written largest to smallest from left to right. However, the numeral for four is not IIII. Instead, the number four is written as IV. Because the one is before the five we subtract it making four. The same principle applies to the number nine, which is written as IX. There are six instances where subtraction is used:  

I can be placed before V (5) and X (10) to make 4 and 9.   
X can be placed before L (50) and C (100) to make 40 and 90.   
C can be placed before D (500) and M (1000) to make 400 and 900.  
Given an integer, convert it to a roman numeral. Input is guaranteed to be within the range from 1 to 3999.  

#### Example 1:

***Input***: 3  
***Output***: "III"
#### Example 2:

***Input***: 4  
Output: "IV"  
#### Example 3:

***Input***: 9  
***Output***: "IX"
#### Example 4:

***Input***: 58  
***Output***: "LVIII"  
***Explanation***: L = 50, V = 5, III = 3.  
#### Example 5:

***Input***: 1994  
***Output***: "MCMXCIV"  
***Explanation***: M = 1000, CM = 900, XC = 90 and IV = 4.
##### code  
```php
<?php

   class test{
       protected  $char_list =
           [
               1 => [
                  "mid" => 'V',
                  "num" => 'I'
               ],
               10 => [
                   "mid" => 'L',
                   "num" => 'X'
               ],
               100 => [
                   "mid" => 'D',
                   "num" => 'C'
               ],
               1000 => [
                   "mid" => '',
                   "num" => 'M'
               ]
           ];
       function intToRoman($num) {
           $res = array();//定义输出结果
           $multiple = 1; //定义分离出数字的位数
           while (1) {
               $temp = ($num % 10) * $multiple;
               $res = array_merge($this->trans($temp, $multiple), $res);
               $num = $num / 10;
               $multiple *= 10;
               if ($num < 10) break;
           }
           $res = array_merge($this->trans(intval($num) * $multiple, $multiple), $res);
           return implode("",$res);
       }
       function trans($num, $mul) {
           echo $num."\n";
           echo $mul."\n";
           $res = array();
              $long = $num - (5 * $mul);
               if ($long >= 0 && $long < (4 * $mul)) {//大于5，加右
                   $res[0] = $this->char_list[$mul]["mid"];
                   for ($i = 0; $i < ($long / $mul); $i++) {
                       array_push($res,$this->char_list[$mul]["num"]);
                   }
               }else if ($long < -$mul) {//小于5，加左
                   $long = abs($long);
                   for ($i = 0; $i < (((5 * $mul) - $long) / $mul); $i++) {
                       array_push($res, $this->char_list[$mul]["num"]);
                   }
               }else {
                   $res = $long == -$mul ? [$this->char_list[$mul]["num"], $this->char_list[$mul]["mid"]] : [$this->char_list[$mul]["num"], $this->char_list[$mul * 10]["num"]];
               }

           return $res;
       }
   }
   $a = new test();
    var_dump($a->intToRoman(1994));


```