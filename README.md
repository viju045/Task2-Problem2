# Task2-Problem2

The head of the linked list contains an unique integer, while nums is a subset on linked list values. The output
needs to be a number of connected components in nums where two values are connected if they appear
consecutively in the linked list


Input: 
head: 0->1->2->3
G = [0, 1, 3]
Output: 2
Explanation: 
0 and 1 are connected, so [0, 1] and [3] are the two connected components.


Input: 
head: 0->1->2->3->4
G = [0, 3, 1, 4]
Output: 2
Explanation: 
0 and 1 are connected, 3 and 4 are connected, so [0, 1] and [3, 4] are the two connected components.



class Solution {
    public int numComponents(ListNode head, int[] G) {
        Set<Integer> Gset = new HashSet<>();
        for (int num : G) {
            Gset.add(num);
        }

        int rst = 0;
        while (head != null) {
            if (Gset.contains(head.val) && (head.next == null || !Gset.contains(head.next.val))) {
                rst++;
            }
            head = head.next;
        }
        return rst;
    }
}
