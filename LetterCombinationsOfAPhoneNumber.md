# Letter Combinations of a Phone Number
Given a string containing digits from 2-9 inclusive, return all possible letter combinations that the number could represent.

A mapping of digit to letters (just like on the telephone buttons) is given below. Note that 1 does not map to any letters.
 ![](./img/question17.png)
####  Example:
 
 ***Input***: "23"  
 ***Output***: ["ad", "ae", "af", "bd", "be", "bf", "cd", "ce", "cf"].  
code
```php
<?php
class Solution {

    //回溯算法
    /**
     * @param String $digits
     * @return String[]
     **/

    public $res = [];
    public $str = "";
    public $list = [
        "2" => ["a","b","c"],
        "3" => ["d","e","f"],
        "4" => ["g","h","i"],
        "5" => ["j","k","l"],
        "6" => ["m","n","o"],
        "7" => ["p","q","r","s"],
        "8" => ["t","u","v"],
        "9" => ["w","x","y","z"]
    ];
    private $c = 1;
    function letterCombinations($digits) {
        if(!$digits) return [];
        $this->_dfs($digits, 0);
        return $this->res;
    }

    private function  _dfs($digits, $step) {
        if ($step == strlen($digits)) {
            $this->res[] = $this->str;
            return;
        }
        $key = substr($digits, $step, 1);
        $chars = $this->list[$key];
        foreach ($chars as $v) {
            $this->str .= $v;
            $this->_dfs($digits, $step + 1);
            $this->str = substr($this->str, 0, strlen($this->str) - 1);
        }
    }
}
$a = new Solution;
var_dump($a->letterCombinations(23));


```