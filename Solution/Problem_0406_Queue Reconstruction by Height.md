# 406. Queue Reconstruction by Height

Suppose you have a random list of people standing in a queue. Each person is described by a pair of integers `(h, k)`, where `h` is the height of the person and `k` is the number of people in front of this person who have a height greater than or equal to `h`. Write an algorithm to reconstruct the queue.

## **Example**

Input: [[7,0], [4,4], [7,1], [5,0], [6,1], [5,2]]

Output: [[5,0], [7,0], [5,2], [6,1], [4,4], [7,1]]

## **Solution**

### ONE

    class Solution {
        public int[][] reconstructQueue(int[][] people) {
            Arrays.sort(people, (a, b) -> a[0] == b[0] ? a[1] - b[1] : b[0] - a[0]);
            int[][] res = new int[people.length][2];
            for(int i = 0; i < people.length; i++) {
                int pos = people[i][1];
                for(int j = i; j > pos; j--) {
                    res[j] = rse[j - 1];
                }
                res[pos] = people[i];
            }
            return res;
        }
    }

### TWO

    class Solution {
        public int[][] reconstructQueue(int[][] people) {
            Arrays.sort(people, (a, b) -> a[0] == b[0] ? a[1] - b[1] : b[0] - a[0]);
            List<int[]> res = new ArrayList<int[]>;
            for(int p: people) {
                res.add(p[1], p);
            }
            return res.toArray(people);
        }
    }
