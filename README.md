# Merge Two Sorted Lists

## Problem

We have two sorted linked lists. We need to merge them into one sorted list.

Example:

```text
list1: 1 → 2 → 4
list2: 1 → 3 → 4

answer: 1 → 1 → 2 → 3 → 4 → 4
```

## How I solved it

I used two pointers for the lists and one pointer for the result.

First I created a temporary node:

```java
ListNode dummy = new ListNode(0);
ListNode current = dummy;
```

I used `dummy` because it makes it easier to start creating the result list.

Then I used a `while` loop:

```java
while (list1 != null && list2 != null)
```

This means that I continue while both lists still have elements.

Inside the loop I compare:

```java
list1.val
list2.val
```

If `list1` has the smaller value, I connect it to `current`:

```java
current.next = list1;
list1 = list1.next;
```

If `list2` has the smaller value, I do the same with `list2`:

```java
current.next = list2;
list2 = list2.next;
```

After that I move `current`:

```java
current = current.next;
```

When one list becomes empty, I don't need to compare anymore. I just connect the remaining list:

```java
if (list1 != null) {
    current.next = list1;
} else {
    current.next = list2;
}
```

At the end I return:

```java
return dummy.next;
```

I return `dummy.next` instead of `dummy` because `dummy` is only a temporary first node.

## Example

For:

```text
list1: 1 → 2 → 4
list2: 1 → 3 → 4
```

I compare the first elements and take the smaller one.

Then I move to the next element in the list from which I took the value.

I repeat this until one list ends.

The final result is:

```text
1 → 1 → 2 → 3 → 4 → 4
```

## Complexity

Time: **O(n + m)**

Space: **O(1)**

## What I learned

I learned how to work with linked lists and the `next` pointer.

The main thing for me was understanding that:

```java
list1 = list1.next;
```

moves to the next element, and:

```java
current.next = list1;
```

connects the current result with the node from `list1`.
