# 739. Daily Temperatures

Given a list of daily temperatures `T`, return a list such that, for each day in the input, tells you how many days you would have to wait until a warmer temperature. If there is no future day for which this is possible, put `0` instead.

## **Example**

For example, given the list of temperatures `T = [73, 74, 75, 71, 69, 72, 76, 73]`, your output should be `[1, 1, 4, 2, 1, 1, 0, 0]`.

## **Solution**

### ONE

    class Solution {
        public int[] dailyTemperatures(int[] T) {
            int[] res = new int[T.length];
            Stack<Integer> s = new Stack<Integer>();
            for(int i = 0; i < T.length; i++) {
                while(!s.isEmpty() && T[i] > T[s.peek()]) {
                    int index = s.pop();
                    res[index] = i - index;
                }
                s.push(i);
            }
            return res;
        }
    }

### TWO

    class Solution {
        public int[] dailyTemperatures(int[] T) {
            int[] res = new int[T.length];
            int max = T.length - 1;
            for(int i = T.length - 2; i >= 0; i--) {
                if(T[i] >= T[max]) {
                    max = i;
                    continue;
                }
                int j = i + 1;
                while(T[i] >= T[j]) {
                    j += res[j];
                }
                res[i] = j - i;
            }
            return res;
        }
    }

## **Note**

Method for Stack()

+ **empty()**

Tests if this stack is empty.

+ **peek()**

Looks at the object at the top of this stack without removing it from the stack.

+ **pop()**

Removes the object at the top of this stack and returns that object as the value of this function.

+ **push(E item)**

Pushes an item onto the top of this stack.

+ **search(Object o)**

Returns the 1-based position where an object is on this stack.
