```java
import java.util.LinkedList;

public class TrainComposition {

    private LinkedList<Integer> linkedList = new LinkedList();
    public void attachWagonFromLeft(int wagonId) {
        linkedList.addFirst(wagonId);
    }

    public void attachWagonFromRight(int wagonId) {
        linkedList.addLast(wagonId);
    }

    public int detachWagonFromLeft() {
        return linkedList.removeFirst();
    }

    public int detachWagonFromRight() {
        return linkedList.removeLast();
    }

    public static void main(String[] args) {
        TrainComposition train = new TrainComposition();
        train.attachWagonFromLeft(7);
        train.attachWagonFromLeft(13);
        System.out.println(train.detachWagonFromRight()); // 7
        System.out.println(train.detachWagonFromLeft()); // 13
    }
}
```
