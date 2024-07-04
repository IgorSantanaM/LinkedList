# LinkedList

This project demonstrates the use of `LinkedList` in C#. It includes operations for adding elements, concatenating lists, converting elements to uppercase, removing items between specific values, and printing the list in reverse order.

## Features

- **Add Elements**: Add elements to a `LinkedList`.
- **Concatenate Lists**: Merge two `LinkedList` objects.
- **Convert to Uppercase**: Change all elements of a `LinkedList` to uppercase.
- **Remove Items Between**: Delete elements in a `LinkedList` between two specified values.
- **Print Reversed List**: Display the elements of a `LinkedList` in reverse order.

## Code Usage

Here's a summary of how the code works:

```csharp
using System;
using System.Collections.Generic;

public class LinkedListTest
{
    private static readonly string[] colors = { "black", "yellow", "green", "blue", "violet", "silver" };
    private static readonly string[] colors2 = { "gold", "white", "brown", "blue", "gray" };

    // set up and manipulate LinkedList objects
    public static void Main(string[] args)
    {
        LinkedList<string> list1 = new LinkedList<string>();

        // add elements to first linked list
        foreach (var color in colors)
            list1.AddLast(color);

        // add elements to second linked list via constructor
        LinkedList<string> list2 = new LinkedList<string>(colors2);

        Concatenate(list1, list2); // concatenate list2 onto list1
        PrintList(list1); // display list1 elements

        Console.WriteLine("\nConverting strings in list1 to uppercase\n");
        ToUppercaseStrings(list1); // convert to uppercase string
        PrintList(list1); // display list1 elements

        Console.WriteLine("\nDeleting strings between BLACK and BROWN\n");
        RemoveItemsBetween(list1, "BLACK", "BROWN");

        PrintList(list1); // display list1 elements
        PrintReversedList(list1); // display list in reverse order
    } // end Main

    // display list contents
    private static void PrintList<T>(LinkedList<T> list)
    {
        Console.WriteLine("Linked list:");
        foreach (T value in list)
            Console.Write("{0} ", value);
        Console.WriteLine();
    } // end method PrintList

    // concatenate the second list on the end of the first list
    private static void Concatenate<T>(LinkedList<T> list1, LinkedList<T> list2)
    {
        foreach (T value in list2)
            list1.AddLast(value); // add new node
    } // end method Concatenate

    // locate string objects and convert to uppercase
    private static void ToUppercaseStrings(LinkedList<string> list)
    {
        LinkedListNode<string> currentNode = list.First;
        while (currentNode != null)
        {
            string color = currentNode.Value; // get value in node
            currentNode.Value = color.ToUpper(); // convert to uppercase
            currentNode = currentNode.Next; // get next node
        } // end while
    } // end method ToUppercaseStrings

    // delete list items between two given items
    private static void RemoveItemsBetween<T>(LinkedList<T> list, T startItem, T endItem)
    {
        LinkedListNode<T> currentNode = list.Find(startItem);
        LinkedListNode<T> endNode = list.Find(endItem);

        // remove items after the start item until we find the last item or the end of the linked list
        while ((currentNode?.Next != null) && (currentNode.Next != endNode))
        {
            list.Remove(currentNode.Next); // remove next node
        } // end while
    } // end method RemoveItemsBetween

    // display reversed list
    private static void PrintReversedList<T>(LinkedList<T> list)
    {
        Console.WriteLine("Reversed List:");
        LinkedListNode<T> currentNode = list.Last;
        while (currentNode != null)
        {
            Console.Write("{0} ", currentNode.Value);
            currentNode = currentNode.Previous; // get previous node
        } // end while
        Console.WriteLine();
    } // end method PrintReversedList
} // end class LinkedListTest
```
## Methods
`PrintList<T>(LinkedList<T> list)`
Displays the contents of a LinkedList.

`Concatenate<T>(LinkedList<T> list1, LinkedList<T> list2)`
Concatenates list2 onto list1.

`ToUppercaseStrings(LinkedList<string> list)`
Converts all string elements in the LinkedList to uppercase.

`RemoveItemsBetween<T>(LinkedList<T> list, T startItem, T endItem)`
Removes items from the LinkedList between startItem and endItem.

`PrintReversedList<T>(LinkedList<T> list)`
Prints the elements of a LinkedList in reverse order.
