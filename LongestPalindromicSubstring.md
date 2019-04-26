# Longest Palindromic Substring
Given a string s, find the longest palindromic substring in s. You may assume that the maximum length of s is 1000.

**Example 1**:

**Input**: "babad"  
**Output**: "bab"  
**Note**: "aba" is also a valid answer.  
**Example 2**:

**Input**: "cbbd"
**Output**: "bb"

#### code
```php
<?php
class Solution {

    /**
     * @param String $s
     * @return String
     */
    public $max = 0;
    public  $res = "";
    function longestPalindrome($s) {
        if (strlen($s) <= 1) {
            return $s;
        }
        for ($i=0;$i<strlen($s);$i++) {
            $this->diffusion($s,$i,$i);
            $this->diffusion($s,$i-1,$i);
        }
        return $this->res;
    }
    public function diffusion($s,$left,$right) {
        while ($left >= 0 && $right <strlen($s) && $s[$left] == $s[$right]) {
            if ($right - $left +1 >$this->max) {
                $this->max = $right - $left +1;
                $this->res = substr($s,$left,$right - $left +1);
            }
            $left--;
            $right++;
        }
    }
}
$test = new Solution();
print_r($test->longestPalindrome('bbbb'));

```




