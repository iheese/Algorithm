```java
    public static int[] findTwoSum(int[] list, int sum) {
        Map<Integer, Integer> map = new HashMap<>();
        for (int i = 0; i < list.length; i++) {
           int c = sum - list[i];
           if(map.containsKey(c)) {
               return new int[]{map.get(c), i};
           }
           map.put(list[i],i);
        }
        return null;
    }
```
