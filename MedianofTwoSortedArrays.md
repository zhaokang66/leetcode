# Median of Two Sorted Arrays
There are two sorted arrays nums1 and nums2 of size m and n respectively.

Find the median of the two sorted arrays. The overall run time complexity should be O(log (m+n)).

You may assume nums1 and nums2 cannot be both empty.

**Example 1**:

nums1 = [1, 3]  
nums2 = [2]

The median is 2.0  
**Example 2**:  

nums1 = [1, 2]
nums2 = [3, 4]

The median is (2 + 3)/2 = 2.5

#### code
```php
<?php
class Solution {

    /**
     * @param Integer[] $nums1
     * @param Integer[] $nums2
     * @return Float
     */
    function findMedianSortedArrays($nums1, $nums2) {
        if (empty($nums1) && empty($nums2)) {
            return 0;
        }
        $new_nums = array_merge($nums1,$nums2);
        sort($new_nums);
        $median = 0;
        $len = count($new_nums);
        if ($len % 2 == 0) {
            $median = ($new_nums[($len/2)] + $new_nums[($len/2-1)]) / 2;
        }else {
            $median = $new_nums[intval($len/2)];
        }
        return $median;
    }
}
$test = new Solution();
 echo  $test->findMedianSortedArrays([1, 2],[3,4]);

```