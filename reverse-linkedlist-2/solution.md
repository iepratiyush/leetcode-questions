# Solution

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public ListNode reverseBetween(ListNode head, int left, int right) {
        ListNode res = new ListNode(0);
        res.next = head;
        ListNode prev1 = null, curr1 = res;
        
        // looping to reach the left node and storing the prev to connect later
        int i = 0;
        for (; i < left; i++) {
            prev1 = curr1;
            curr1 = curr1.next;
        }

        // reverse list
        ListNode prev2 = prev1, curr2 = curr1, next;
        for (; i <= right; i++) {
            next = curr2.next;
            curr2.next = prev2;
            prev2 = curr2;
            curr2 = next;
        }
        
        // connect
        prev1.next = prev2;
        curr1.next = curr2;
        
        return res.next;
    }
}
```