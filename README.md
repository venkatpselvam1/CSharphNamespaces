# CSharphNamespaces
* Array.Sort(arr)    // using System;
* Array.Sort(arr, new Comparer());
* String.Concat(str.OrderBy(c => c)) => to order the char in the string
* dict.ContainsKey()//using System.Collections.Generic;
* when you want to know isFirstBool, try to set the first value instead of this bool. e.g. max of array, set the max value as arr[0] and start the loop.
* using System.Linq;
* IList<IList<int>> ans = new List<IList<int>>();
* To copy a list in C# => list.ToList();
* To define and use multidimersionl array. var arr = new int[,]{ {1,2,3}, {4,5,6}}; (or) empty array var arr = new int[2,3];
* to convert a no to binary string in C# => Convert.ToString(45, 2);
* To remove the last of n index from the linked list, use two pointer method. Pointer 1: current(starts from head to tail), Pointer 2: current - n-th node https://leetcode.com/problems/3sum/
* System.Collections.Generic; Stack<int>, Push, Pop, Peek, Count 
* To avoid null check for linked list, we can use dummy. Dummy will have any value. Whenever we find new element, we will add it to dummy.next. When we need to return the ans, use dummy.next. https://leetcode.com/problems/merge-two-sorted-lists/submissions/
* string.Insert(index, anotherString) => e.g. "abcd".Insert(2, "XX") "abXXcd"
* HashMap<string> instead of List<string> for duplicate removal scenario. To convert to HashMap<string> to List<string> use new List<string>(h) where h is new HashMap<string>
* var mod = 1e9 + 7; to return the ans in modulo 10 power 9 + 7. Note: this no is the highest prime on in the int32 range. https://www.geeksforgeeks.org/modulo-1097-1000000007/
* For O(Log n) Search (Search a no in sorted array,) => To find mid use mid = start +(end - start)/2; So that, it will avoid infinite loop.
  After that you can go with (start, mid-1) or (mid+1, end)
  
 # Big O Cheat sheet
 * https://www.bigocheatsheet.com/
 * Order of sorting algorithem to remeber
 * 1. Bubble, Insertion, Selection                => O(n^2)                             => O(1)
 * 2. Shell (variation of insertion)              => O(n (log n)^2)                     => O(1)
 * 3. Merge and quick sort (divide and conquer)   => O(n log n)                         => O(n) , O(log n)
 * 4. Redix, couning, Bucket sort                 => K redi(x) nk, countingbucket n+k   => redix O(n+k), Bucket O(n), counting O(k)

  
 # Useful links
  * https://www.programiz.com/dsa/quick-sort

 # Comparer
  public class Comparer : IComparer<string, string>{
    public int Compare(string a, string b){
      return a.Length - b.Length;
    }
  }
