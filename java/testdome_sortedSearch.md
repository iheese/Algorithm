```java
    public static int countNumbers(int[] sortedArray, int lessThan) {
        int low = 0;
        int high = sortedArray.length - 1;
        int count = 0;

        while (low <= high) {
            int mid = low + (high - low) / 2;

            if (sortedArray[mid] < lessThan) {
                // 현재 중간 요소가 lessThan보다 작으면 mid 이하의 요소는 모두 작습니다.
                count = mid + 1;
                low = mid + 1;
            } else {
                // 현재 중간 요소가 lessThan보다 크거나 같으면 mid 이상의 요소만 고려합니다.
                high = mid - 1;
            }
        }

        return count;
    }

```
