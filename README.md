# Task2-Problem2

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


Java:
first:

public int numComponents(ListNode head, int[] G) {
    if (G.length == 1) {
        return 1;
    }
    int count = 0;
    int t = 0;
    while (head != null) {
        boolean c = contain(G, head.val);
        if (c) {
            t++;
        } else {
            count += (t == 0 ? 0 : 1);
            t = 0;
        }
        head = head.next;
    }
    if (t != 0) {
        count++;
    }
    return count;
}
public boolean contain(int[] G, int v) {
    for (int t : G) {
        if (t == v) {
            return true;
        }
    }
    return false;
}


Second:
public int numComponents(ListNode head, int[] G) {
    Set<Integer> setG = new HashSet<>();
    for (int i: G) setG.add(i);
    int res = 0;
    while (head != null) {
        if (setG.contains(head.val) && (head.next == null || !setG.contains(head.next.val))) res++;
        head = head.next;
    }
    return res;
}
