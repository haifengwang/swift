swift
=====
##常用的类型   

  Swift版中包含C和Object-C所有类型`Int` 整形，`Double` 和 `Float` 浮点型，`Bool`布尔型，`String` 字符型，Swift也提供两种强大的集合类型，`Array` 和`Dictionary`，成为集合类型。

###Int 类型 
   
  Integers类型是所有类型的基础。Swift提供了有符合无符号类型的8，16，32，64形式。这种命名和C语言比较接近。如无符号8位，`UInt8`,32-bit表示为`Int32`。Int在32和64位系统下，会自动转换为操作系统对应的位数。
  
  Int类型的界
  
  可以通过`min`和`max`属性获取Int类型的界。
  `let minValue = UInt8.min   // minValue is equal to 0, and is of type UInt8` 
  `let maxValue = UInt8.max  // maxValue is equal to 255, and is of type UInt8`
  
###浮点型 
 **Float** 和 **Double**  `Float`代表32位精度数字，`Double`代表64位精度精度数字。 
 >注： `Double`的精确度可以达到小数点后15位，而`Float`只能达到6位。  
 
 不同进制数字表示方式  
 
 + 十进制不加任何前缀 
 + 二进制以`0b`为前缀 
 + 八进制以`0o`为前缀 
 + 16进制以`0x`为前缀 
 
 ``` 
let decimalInteger = 17           // 17 十进制
let binaryInteger = 0b10001       // 17 用二进制的表示
let octalInteger = 0o21           // 17 八进制
let hexadecimalInteger = 0x11     // 17 16进制 
 ```  
 **typealias** 给类型一个别名，别名申明成功后，可以使用该类型的方法 `typealias AudioSample = UInt16`

###  布尔类型 
Swift提供了一种基础的Boolean类型，布尔类型值也称为逻辑值，因为它仅存在`true`和`flase`.（有别于OC中使用YES和NO）

 布尔类型 **Bool**   `var isNew:Bool=true` 
 
 Swift是类型安全的，不允许非布尔类型代替布尔类型做逻辑运算。(区别于javascript类型的语言) 
 
 ``` 
let i = 1
if i {
    // 这个例子不会编译通过
}
 ```  
以上可以用 `if 1==1{}` 逻辑运算方式进行 

###元组(Tuples) 
元组(Tuples)组织多个值为一个复合的不可变的有序集合。元组中可以包含任意类型。
Eg: `let http404Error=(404,"Not Found")`  

获取元组的值：
`let (statusCode, statusMessage) = http404Error` 

如果只想获得其中其中需要的`let (justTheStatusCode, _) = http404Error`  

**_**代表的意义是忽略部分。 
>注：元组和python中基本相似，如果元组只包含一个元素，在Swift中`var atuples=(22)`,而在python确是另一种方式。`_`占位符，在`go`中应用相当广泛。  

Swift中的元组还可以给元组中元素命名

如：`let http200Status = (statusCode: 200, description: "OK") ` 

访问方式: 
`println("The status code is \(http200Status.statusCode)")`

###字符串
字符串是一个有序序列的字符的集合 

字符串类型 **String** `var df="Hello World"` 
   
+  字符串链接 **+**  ```var name="ddd"; var user="ad"; var username=user+naem```  

+ 插入的方式链接 `var greet="Welcome \(name)!"`  
+ isEmpty 判断是否为空字符串  
   
 ``` 
var copyString=""

if copyString.isEmpty {
    println("这是一个空！ß")
} 
```

+ For character in "" //遍历字符串的字符   
 
``` 
  for char in "这是一个错误"{
    println(char)
  } 

```
+ countElements("") //统计字符串的数量   

``` 
var result="中华人民共和国"
println(countElements(result)); 

``` 
+ == 是否相等；hasSuffixn是否包含后缀 hasPrefix 是否包含前缀  
+ uppercaseString 大写；lowercaseString 小写 
