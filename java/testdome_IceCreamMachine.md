```java
    public List<IceCream> scoops() {
        if(ingredients.length == 0 || toppings.length == 0) {
            return Collections.emptyList();
        }
        List<IceCream> iceCreamList = new ArrayList<>();
        for (String ingredient : ingredients) {
            for (String topping : toppings) {
                IceCream ice = new IceCream(ingredient, topping);
                iceCreamList.add(ice);
            }
        }
        return iceCreamList;
    }
```

- 내 답

