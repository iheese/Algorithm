```java
public class UserInput {

    public static class TextInput {
        StringBuffer sb = new StringBuffer();

        public void add(char c) {
            sb.append(c);
        }
        public String getValue() {
            return sb.toString();
        }
    }

    public static class NumericInput extends TextInput {

        public void add(char c) {
            if(Character.isDigit(c)) {
                sb.append(c);
            }
        }
    }

    public static void main(String[] args) {
        TextInput input = new NumericInput();
        input.add('1');
        input.add('a');
        input.add('0');
        System.out.println(input.getValue());
    }
}
```
