# Generate Parentheses
Given n pairs of parentheses, write a function to generate all combinations of well-formed parentheses.

For example, given n = 3, a solution set is:
```
[
  "((()))",
  "(()())",
  "(())()",
  "()(())",
  "()()()"
]
```
code
```php
<?php$right) {
            $this->_gen($left, $right + 1, $num, $ret.")");
        }
    }
class Solution {
    public $list = [];
    function _gen($left, $right, $num, $ret) {
        if ($left == $num && $right == $num) {
            array_push($this->list, $ret);
            return;
        }
        if ($left < $num) {
            $this->_gen($left + 1, $right, $num, $ret."(");
        }
        if ($right < $num && $left > 
    function generateParenthesis($n) {
        $this->_gen(0, 0, $n, "");
        return $this->list;
    }
}

$a = new Solution();
print_r($a->generateParenthesis(3));
```
