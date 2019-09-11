# Remove Nth Node From End of List
Given a linked list, remove the n-th node from the end of list and return its head.

#### Example:
```
Given linked list: 1->2->3->4->5, and n = 2.

After removing the second node from the end, the linked list becomes 1->2->3->5.
```
code
```php
<?php
function removeNthFromEnd($head, $n) {
    $dummy = new ListNode(0);
    $dummy->next = $head;
    $fast = $dummy;
    $slow = $dummy;
    for($i=0;$i<$n+1;$i++){
        $fast = $fast->next;
    }
    while($fast!=null){
        $fast = $fast->next;
        $slow = $slow->next;
    }
    $slow->next = $slow->next->next;
    return $dummy->next;

}
```