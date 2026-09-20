# Ex7 Removal of Nodes with a Specific Value from a Linked List
## AIM:
To write a java  program that removes all nodes from a linked list whose value matches a given integer (val) and returns the new head of the modified linked list.

## Algorithm
1. Start the program.
2. Create dummy head.
3. Set prev = dummy, curr = head.
4. Traverse list.
5. Move curr each step.
6. Return dummy.next as updated head.
7. Stop the program.

## Program:
```
/*
program that removes all nodes from a linked list whose value matches a given integer (val) and returns the new head of the modified linked list.
Developed by: Yuvaram S
RegisterNumber: 212224230315
*/

import java.util.*;

class ListNode {
    int val;
    ListNode next;

    ListNode(int val) {
        this.val = val;
    }
}

class Solution {
    public ListNode removeElements(ListNode head, int val) {
        ListNode dummy = new ListNode(0);
        dummy.next = head;
        ListNode prev = dummy, curr = head;

        while (curr != null) {
            if (curr.val == val) {
                prev.next = curr.next; 
            } else {
                prev = curr; 
            }
            curr = curr.next; 
        }

        return dummy.next; 
    }
}

public class Main {

    public static ListNode buildList(int[] arr) {
        if (arr.length == 0) return null;
        ListNode head = new ListNode(arr[0]);
        ListNode current = head;
        for (int i = 1; i < arr.length; i++) {
            current.next = new ListNode(arr[i]);
            current = current.next;
        }
        return head;
    }

    public static String listToString(ListNode head) {
        List<Integer> result = new ArrayList<>();
        while (head != null) {
            result.add(head.val);
            head = head.next;
        }
        return result.toString(); 
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        String input = scanner.nextLine().replaceAll("\\s", "");
        int[] nums = Arrays.stream(input.split(","))
                           .mapToInt(Integer::parseInt)
                           .toArray();


        int val = scanner.nextInt();
        ListNode head = buildList(nums);
        Solution solution = new Solution();
        ListNode updated = solution.removeElements(head, val);
        System.out.println(listToString(updated));

        scanner.close();
    }
}

```

## Output:

<img width="711" height="378" alt="image" src="https://github.com/user-attachments/assets/70f588ac-de12-42b9-ae1e-38a456093a03" />

## Result:
The java program successfully removes all nodes with the specified value (val) from the linked list and returns the new head.
