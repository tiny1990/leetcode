# 146. LRU缓存机制

TLDR
```
LRUCache cache = new LRUCache( 2 /* 缓存容量 */ );

cache.put(1, 1);
cache.put(2, 2);
cache.get(1);       // 返回  1
cache.put(3, 3);    // 该操作会使得密钥 2 作废
cache.get(2);       // 返回 -1 (未找到)
cache.put(4, 4);    // 该操作会使得密钥 1 作废
cache.get(1);       // 返回 -1 (未找到)
cache.get(3);       // 返回  3
cache.get(4);       // 返回  4

```


```java
class LRUCache {

        public int get(int key) {
        }
        public void put(int key, int value) {
        }

}
```

## 解题思路
map存储key，value是上一个node，

## 题解

```java
class LRUCache {

    // 定义链表结构
    class Node {
        int k;
        int v;
        Node next;

        public Node(int k, int v, Node next) {
            this.k = k;
            this.v = v;
            this.next = next;
        }
    }

    private int capacity;
    private int size;
    private Map<Integer,Node> keyToPre;
    private Node dummy;
    private Node tail;

    public LRUCache(int capacity) {
        this.capacity = capacity;
        this.keyToPre = new HashMap<>();

        dummy = new Node(-1,-1, null);
        tail = dummy;
    }

    public int get(int key) {
        if (!keyToPre.containsKey(key)) {
            return -1;
        }
        moveTotail(key);
        return tail.v;
    }

    public void put(int key, int value) {
        if(get(key) != -1) {
            Node pre = keyToPre.get(key);
            pre.next.v = value;
            return;
        }

        if (size <  capacity) {
            size++;
            Node n = new Node(key,value,null);
            tail.next = n;
            keyToPre.put(key,tail);
            tail = n;
        } else {
            Node first = dummy.next;
            keyToPre.remove(first.k);

            first.k = key;
            first.v = value;

            keyToPre.put(key,dummy);
            moveTotail(key);
        }
    }

    private void moveTotail(int key) {
        Node preNode = keyToPre.get(key);
        Node current = preNode.next;

        if (tail == current) {
            return;
        }
        preNode.next = preNode.next.next;
        tail.next = current;

        if(preNode.next != null) {
            keyToPre.put(preNode.next.k,preNode);
        }
        keyToPre.put(current.k, tail);
        tail = current;
    }

}
```
