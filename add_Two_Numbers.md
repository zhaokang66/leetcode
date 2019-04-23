# Add Two Numbers
You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order and each of their nodes contain a single digit. Add the two numbers and return it as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.

### Example:

```
Input: (2 -> 4 -> 3) + (5 -> 6 -> 4)
Output: 7 -> 0 -> 8
```
Explanation: 342 + 465 = 807

```php

```




##### other code
```php
<?php
/**
 * Definition for a singly-linked list.
 * class ListNode {
 *     public $val = 0;
 *     public $next = null;
 *     function __construct($val) { $this->val = $val; }
 * }
 */
class Solution {

    private $carry = 0;
    /**
     * @param ListNode $l1
     * @param ListNode $l2
     * @return ListNode
     */
    function addTwoNumbers($l1, $l2) {
        $list = new ListNode($l1->val + $l2->val + $this->carry);

        if($list->val > 9) {
            $list->val = $list->val % 10;
            $this->carry = 1;
        }else {
            $this->carry = 0;
        }

        if($l1->next || $l2->next) {
            $l1->next = $l1->next != null ? $l1->next : 0;
            $l2->next = $l2->next != null ? $l2->next : 0;
        }
        $list->next = (is_null($l1->next) && is_null($l2->next)) ? null : $this->addTwoNumbers($l1->next,$l2->next);
        if($this->carry > 0) {
            $list->next = $this->addTwoNumbers(0,0);
        }
        return $list;

    }
}
```

#### operation result
Runtime: 36 ms, faster than 45.76% of PHP online submissions for Add Two Numbers.
Memory Usage: 14.9 MB, less than 6.98% of PHP online submissions for Add Two Numbers.