# fourSum 

Given an array nums of n integers and an integer target, are there elements a, b, c, and d in nums such that a + b + c + d = target? Find all unique quadruplets in the array which gives the sum of target.

#### example
```
Given array nums = [1, 0, -1, 0, -2, 2], and target = 0.

A solution set is:
[
  [-1,  0, 0, 1],
  [-2, -1, 1, 2],
  [-2,  0, 0, 2]
]

```
code
```php
<?php

function fourSum($nums, $target) {
    if (!$nums) return [];
    sort($nums);
    $res = [];
    for ($i = 0; $i < count($nums) -3; $i++) {
        if ($i > 0 && count($nums) != 4 && $nums[$i] == $nums[$i - 1]) continue;
        for ($j = $i + 1; $j < count($nums) - 2; $j++) {
            if ($j > 0 && count($nums) != 4 && $j != $i + 1 && $nums[$j] == $nums[$j - 1]) continue;
            $left = $j + 1;
            $right = count($nums) - 1;
            while ($left < $right) {
                $sum = $nums[$i] + $nums[$j] + $nums[$left] +$nums[$right];
                if ($sum == $target) {
                    array_push($res, [$nums[$i], $nums[$j], $nums[$left], $nums[$right]]);
                    while ($left < $right && $nums[$left] == $nums[$left + 1]) $left++;
                    while ($left < $right && $nums[$right] == $nums[$right - 1]) $right--;
                    $left++;
                    $right--;
                }else if ($sum > $target) {
                    $right--;
                }else {
                    $left++;
                }
            }
        }
    }
    return $res;
}
print_r(fourSum([-1,0,1,2,-1,-4],-1));//-4 -1 -1 0 1 2
/*-4 -1 -1 0
-4 -
*/
```