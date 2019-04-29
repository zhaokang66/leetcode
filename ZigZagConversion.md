# ZigZag Conversion
The string **"PAYPALISHIRING"** is written in a zigzag pattern on a given number of rows like this: (you may want to display this pattern in a fixed font for better legibility)
```
P   A   H   N
A P L S I I G
Y   I   R
```
And then read line by line: **"PAHNAPLSIIGYIR"**

Write the code that will take a string and make this conversion given a number of rows:

`string convert(string s, int numRows);`  
#### Example 1:

**Input**: s = "**PAYPALISHIRING**", numRows = 3  
**Output**: "**PAHNAPLSIIGYIR**"
#### Example 2:

**Input**: s = "PAYPALISHIRING", numRows = 4  
**Output**: "PINALSIGYAHRPI"
#### Explanation:
```
P     I    N
A   L S  I G
Y A   H R
P     I
```

#### code 
```php
<?php
class Solution {

    /**
     * @param String $s
     * @param Integer $numRows
     * @return String
     */
    function convert($s, $numRows) {
        if (strlen($s) == 1 || $numRows == 1) {
            return $s;
        }
        $pre = -1;
        $ret = [];
        $flag = "down";
        for ($i = 0; $i < strlen($s); $i++) {
            if ($flag == "down") {
                $ret[$pre + 1][] = $s[$i];
                $pre++;
                if ($pre == $numRows - 1) {
                    $flag = "up";
                }
            }else if ($flag == "up") {
                $ret[$pre - 1][] = $s[$i];
                $pre--;
                if ($pre == 0) {
                    $flag = "down";
                }
            }
         }
         return implode("",array_map(function($a){return implode("",$a);},$ret));
    }
}
$test = new Solution();
print_r($test->convert("PAYPALISHIRING",3));
```