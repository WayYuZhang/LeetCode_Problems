# 347. Top K Frequent Elements

Given a non-empty array of integers, return the **_k_** most frequent elements.

## **Example**

**Example 1:**

**Input:** nums = [1,1,1,2,2,3], k = 2

**Output:** [1,2]

**Example 2:**

**Input:** nums = [1], k = 1

**Output:** [1]

## **Solution**

### ONE

    class Solution {
        public List<Integer> topKFrequent(int[] nums, int k) {
            Map<Integer, Integer> m = new HashMap<Integer, Integer>();
            List<Integer>[] bucket = new List[nums.length + 1];
            List<Integer> res = new LinkedList<Integer>();
            for(int i : nums) {
                m.put(i, m.getOrDefault(i, 0) + 1);
            }
            for(int i : m.keySet()) {
                int count = m.get(i);
                if(bucket[count] == null)
                    bucket[count] = new LinkedList<Integer>();
                bucket[count].add(i);
            }
            for(int i = bucket.length - 1; i > 0 && k > 0; i--) {
                if(bucket[i] != null) {
                    List<Integer> l = bucket[i];
                    res.addAll(l);
                    k -= l.size();
                }
            }
            return res;
        }
    }

### TWO

    class Solution {
        public List<Integer> topKFrequent(int[] nums, int k) {
            Map<Integer, Integer> m = new HashMap<Integer, Integer>();
            PriorityQueue<Integer> heap = new PriorityQueue<Integer>((n1, n2) -> m.get(n1) - m.get(n2));
            List<Integer> res = new LinkedList<Integer>();
            for(int i : nums) {
                m.put(i, m.getOrDefault(i, 0) + 1);
            }
            for(int i : m.keySet()) {
                heap.add(i);
                if(heap.size() > k)
                    heap.poll();
            }
            while(heap.isEmpty()) {
                res.add(heap.poll());
            }
            Collections.reverse(res);
            return res;
        }
    }

## **Note**

Method for **PriorityQueue**

+ PriorityQueue(PriorityQueue<? extends E> c)

Creates a PriorityQueue containing the elements in the specified priority queue.

+ add(E e)

Inserts the specified element into this priority queue.

+ peek()

Retrieves, but does not remove, the head of this queue, or returns null if this queue is empty.

+ poll()

Retrieves and removes the head of this queue, or returns null if this queue is empty.
