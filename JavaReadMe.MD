# JAVA
## Minor things

--How to quicly print an array

```
var arr = new int[]{1, 23, 1, -1, 9};
System.out.println(Arrays.toString(arr));
```

--How to check a character exists in a string

```
var str = "venkatesan";
if(str.indexOf('z') != -1) System.out.println("char z not present in string " + str);
```

--How to convert a string to integer

```
String strNum = "12345";
int intNum = Integer.parseInt(strNum);//This method throws NumberFormatException if strNum is not a valid number
```

Hash set to Integer array
```
var ans = new HashSet<Integer>();
ans.add(1);ans.add(2);ans.add(11);ans.add(12);
ans.stream().mapToInt(Number::intValue).toArray();
```

HashMap Iterate Keys

```
var map = new HashMap<Integer, String>();
map.put(1, "test");map.put(2, "tes1t");map.put(3, "test4");map.put(3, "rest");
for(var k: map.keySet()) System.out.println(k+" -> " + map.get(k));
```

--Count character in string

```
private int[] countChars(String str){
    var ans = new int[26];
    for(var item: str.toCharArray()) ans[item-'a']++;
    return ans;
}
```


## Comparator in sort JAVA
```
        var arr1 = new int[]{1,2,3,4,11,12,22,34,1,2,3,4};
        Integer[] boxed = Arrays.stream(arr1).boxed().toArray(Integer[]::new);
        Arrays.sort(boxed, (a, b) -> b - a);
        System.out.println(Arrays.toString(boxed));
```

```
       var arr = new String[]{"abc", "abcd", "abfdfd"};
        Arrays.sort(arr, (a,b) -> {
            return b.length() - a.length();
        });
        System.out.println(Arrays.toString(arr));
```

```
        var arr = new int[][] { {1, 0}, {0,1}, {1,99}, {100, 1}, {1, 1001} };
        Arrays.sort(arr, (a, b) -> {
            return b[1] - a[1];
        } );
        for(var row: arr) System.out.println(Arrays.toString(row));
```

 ```
  public class ArrComparator implements Comparator<int[]>{
      public int compare(int[] a, int[] b){
          return a[1] - b[1];
      }
  }
  // Arrays.sort(arr1, new ArrComparator());
 ```
 ## Stack in JAVA
  ```
  var st = new Stack<Character>();
  st.push('A');st.push('B');st.push('C');
  var last = st.pop();
  st.empty();
  st.size();
  ```
 ## Priority Queue in JAVA

```
        var arr = new int[][] { {1, 0}, {0,1}, {1,99}, {100, 1}, {1, 1001} };
        var pq = new PriorityQueue<int[]>((a, b) -> {
            return b[1] - a[1];
        });
        for(var item: arr) pq.add(item);
        while(!pq.isEmpty()) System.out.println(Arrays.toString(pq.remove()));

```
 ```
 var pq = new PriorityQueue<Integer>();
 pq.add(5);
 var last = pq.remove();
 if(pq.isEmpty()) System.out.println("Priority Queue is empty");

 // Priority Queue with custom comparator
 var pq = new PriorityQueue<int[]>(new ArrComparator());
 pq.add(new int[]{0,0,1};
 var curr = pq.remove();

 public class ArrComparator implements Comparator<int[]>{
 public int compare(int[] a, int [] b){
 return a[2] - b[2];
 }
 }
 ```
 ## Tree Map in JAVA
  TreeMap is Kind of dictionary data structure, but the keys are stored in sorted order. So, if you add any new key, that key will placed in sorted order. Also we have method like higherEntry(), lowerEntry() to fetch the before and after nodes for the given value.
  https://leetcode.com/problems/count-integers-in-intervals/submissions/ This problem is better solved with TreeMap.

## Union Find

```
    private void test(){
        var uf = new UnionFind(10);
        System.out.println(uf.union(1, 2));
        System.out.println(uf.union(1, 3));
        System.out.println(uf.union(1, 4));
        System.out.println(uf.union(1, 5));
        System.out.println(uf.union(0, 6));
        System.out.println(uf.union(0, 7));
        System.out.println(uf.union(0, 8));
        System.out.println(uf.union(0, 9));
        System.out.println(uf.union(0, 1));
        uf.print();
    }

    public class UnionFind{
        int[] parent;
        int[] w;
        int n;
        public UnionFind(int nn){
            this.n = nn;
            this.parent = new int[n];
            this.w = new int[n];
            for(int i = 0; i < n; i++){
                this.parent[i] = i;
                this.w[i] = 1;
            }
        }
        public boolean union(int a, int b){
            var r1 = find(a);
            var r2 = find(b);
            if(r1 == r2) return false;//already union
            if(w[r1] >= w[r2]){
                w[r1] += w[r2];
                parent[r2] = r1;
            }else{
                w[r2] += w[r1];
                parent[r1] = r2;
            }
            return true;//union is made
        }
        public int find(int a){
            if(a != parent[a]){
                parent[a] = find(parent[a]);
            }
            return parent[a];
        }
        public void print(){
            System.out.println("-----------");
            System.out.println("Node " + n);
            System.out.println(Arrays.toString(parent));
            System.out.println(Arrays.toString(w));
            System.out.println("-----------");
        }
    }
```

 ## LRU cache -> Least Recently Used
    the cache will have the capacity, once the capacity is reached we remove the least used key from the list. For this, we will maintain a double linked list and rmeove and keep the nodes in sorted(orderedw way).
  When any key is accessed, we move the key to front. so Automatically, remaining key will be moved away to tail making it easier to remove.
