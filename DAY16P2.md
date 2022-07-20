# Min Stack
---
- ## Question:
> Design a stack that supports push, pop, top, and retrieving the minimum element in constant time.
---
- ## Example:
> Input
["MinStack","push","push","push","getMin","pop","top","getMin"]
[[],[-2],[0],[-3],[],[],[],[]]
> 
> Output
[null,null,null,null,-3,null,0,-2]
---
- ## Solution:
**Code :**
```java
class MinStack {
    Stack<Integer> st=new Stack<>();
    int min=Integer.MAX_VALUE;
    public void push(int val) {
        if(val<=min)
        {
            st.push(min);
            min=val;
        }
        st.push(val);
    }
    
    public void pop() {
        if(st.peek()==min)
        {
            st.pop();
            min=st.pop();
        }
        else
        {
            st.pop();
        }
    }
    
    public int top() {
        return st.peek();
    }
    
    public int getMin() {
        return min;
    }
}
