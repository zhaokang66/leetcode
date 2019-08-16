# threeSum
Given an array nums of n integers, are there elements a, b, c in nums such that a + b + c = 0? Find all unique triplets in the array which gives the sum of zero.

***Note***:

The solution set must not contain duplicate triplets.

####Example:
```
Given array nums = [-1, 0, 1, 2, -1, -4],

A solution set is:
[
  [-1, 0, 1],
  [-1, -1, 2]
]
```
code
```php
<?php
function threeSum($nums) {
    if (!$nums) return [];
    sort($nums);
    $res = [];
//    print_r($nums);
//    die();
    for ($i = 0; $i < count($nums) - 2; $i++) {
        if ($i > 0 && $nums[$i] == $nums[$i - 1]) continue;//跳过数组中重复元素
        $left =  $i + 1;
        $right = count($nums) - 1;
        $need = 0 - $nums[$i];
        while ($left < $right) {
            if ($nums[$left] + $nums[$right] == $need) {
                array_push($res, [$nums[$i], $nums[$left], $nums[$right]]);
                while ($left < $right && $nums[$left] == $nums[$left + 1]) $left++;
                while ($left < $right && $nums[$right] == $nums[$right - 1]) $right--;
                $left++;
                $right--;
            }else if ($nums[$left] + $nums[$right] > $need) {
                $right--;
            }else {
                $left++;
            }
        }

    }
    return $res;

}

var_dump(threeSum([-1, 0, 1, 1, -1, -4]));
```
