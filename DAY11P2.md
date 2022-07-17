# Bus Routes
---
- ## Question:
> You are given an array routes representing bus routes where routes[i] is a bus route that the ith bus repeats forever.
> 
> For example, if routes[0] = [1, 5, 7], this means that the 0th bus travels in the sequence 1 -> 5 -> 7 -> 1 -> 5 -> 7 -> 1 -> ... forever.
> 
> You will start at the bus stop source (You are not on any bus initially), and you want to go to the bus stop target. You can travel between bus stops by buses only.
> 
> Return the least number of buses you must take to travel from source to target. Return -1 if it is not possible.
---
- ## Example:
> Input: routes = [[1,2,7],[3,6,7]], source = 1, target = 6
> 
> Output: 2
> 
> Explanation: The best strategy is take the first bus to the bus stop 7, then take the second bus to the bus stop 6.
---
- ## Solution:
**Code :**
```java
class Solution {
    public int numBusesToDestination(int[][] routes, int source, int target) {
        int N = routes.length;
        if(source == target){
            return 0; 
        }
        
        HashMap<Integer,ArrayList<Integer>> map = new HashMap<>();
        for( int bus = 0 ; bus < routes.length ; bus++ ){
            for( int busStand : routes[bus] ){
                if( !map.containsKey(busStand) ){
                    map.put( busStand , new ArrayList<Integer>() );
                }
                ArrayList<Integer> bs = map.get(busStand);
                bs.add(bus);                
            }
        }
        
        boolean[] busVisited = new boolean[N];
        boolean[] standVisited = new boolean[100001];
        LinkedList<Integer> queue = new LinkedList<>();
        int noOfBuses = 0;
    
        queue.addLast(source);
        standVisited[source] = true;
        
        
        while( queue.size() > 0 ){
            int size = queue.size();
            while( size-- > 0 ){
                Integer busStand = queue.removeFirst();
                if( busStand == target ){
                    return noOfBuses;
                }
                ArrayList<Integer> buses = map.get(busStand);
                for( int bus : buses ){
                    if( busVisited[bus] ){
                        continue;
                    }else{
                        busVisited[bus] = true;
                    }
                    int[] busStands = routes[bus];
                    for( int bs : busStands ){
                         if( standVisited[bs] ){
                            continue;
                        }
                        queue.addLast( bs );
                        standVisited[bs] = true;
                    }
                }
            }
            noOfBuses++;
        }
        return -1;
    }
}
