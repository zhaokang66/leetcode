# Two Sum

Given an array of integers, return indices of the two numbers such that they add up to a specific target.
You may assume that each input would have exactly one solution, and you may not use the same element twice.

### Example:

Given nums = [2, 7, 11, 15], target = 9,

Because nums[0] + nums[1] = 2 + 7 = 9,
return [0, 1].

#### code:
```php
<?php
    class Solution {
        function twoSum($nums,$target) {
            $result = array();
            for($i=0;$i<count($nums);$i++) {
                for($j=0;$j<count($nums);$j++) {
                    if($i!==$j&& ($nums[$i]+$nums[$j])==$target) {
                        array_push($result,$i,$j);
                        break 2;
                    }
                }
            }
            if(!empty($result)) {
                return $result;
            }else {
                return "没有匹配到";
            }
        }
    }
    $test = new Solution();
    var_dump($test->twoSum([4,8,4,2,5],10));

```
### operation result

Runtime: 3956 ms, faster than 5.04% of PHP online submissions for Two Sum.
Memory Usage: 15.7 MB, less than 77.36% of PHP online submissions for Two Sum.

#### other code
```php
<?php
    class Solution {
        function twoSum($nums,$target) {
            $map = [];
            for($i=0;$i<count($nums);$i++) {
                $diff = $target-$nums[$i];
                if(isset($map[$diff])) {
                    return [$map[$diff],$i];
                }
                $map[$nums[$i]] = $i;
            }
            return "没有找到";
        }
    }
    $test = new Solution();
    var_dump($test->twoSum([4,8,4,2,5],10));
```