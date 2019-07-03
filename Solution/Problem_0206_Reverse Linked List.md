# 206. Reverse Linked List

Reverse a singly linked list.

## **Example**

**Input:** 1->2->3->4->5->NULL

**Output:** 5->4->3->2->1->NULL

## **Solution**

### ONE

    /**
     * Definition for singly-linked list.
     * public class ListNode {
     *     int val;
     *     ListNode next;
     *     ListNode(int x) { val = x; }
     * }
     */
    class Solution {
        public ListNode reverseList(ListNode head) {
            ListNode pre = null;
            ListNode cur = head;
            while(cur != null) {
                ListNode tmp = cur.next;
                cur.next = pre;
                pre = cur;
                cur = tmp;
            }
            return pre;
        }
    }

### TWO

    class Solution {
        public ListNode reverseList(ListNode head) {
            if(head == null || head.next == null)
                return head;
            ListNode p = reverseList(head.next);
            head.next.next = head;
            head.next = null;
            return p;
        }
    }
