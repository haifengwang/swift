函数是包含一段可以执行代码的语句块。对这个语句块命名，在需要的地方通过名称调用。Swift 的函数是 C 风格式的，在定义上足够灵活。

###函数的定义和调用
定义一个函数,可以定义一个或多个命名类型的参数,或一个命名的类型的返回值

```
//申明一个名为sayHello,有两个参数的，返回值为String类型
func sayHello(personName: String,anthorName:String) -> String {
    let greeting = "Hello, " + personName + " and "+anthorName+"!"
    return greeting
}
//调用
println(sayHello("alex","alice")) 
//无返回值类型
func sayGreet(){
    println("问候！")
}
//调用
sayGreet()
``` 
###函数多返回值 
可以使用 `tuple` 类型作为函数的返回类型返回多个值。

```
//定义一个统计字符的函数
func count(string: String) -> (vowels: Int, consonants: Int, others: Int) {
    var vowels = 0, consonants = 0, others = 0
    for character in string {
        switch String(character).lowercaseString {
        case "a", "e", "i", "o", "u":
            ++vowels
        case "b", "c", "d", "f", "g", "h", "j", "k", "l", "m",
        "n", "p", "q", "r", "s", "t", "v", "w", "x", "y", "z":
            ++consonants
        default:
            ++others
        }
    }
    return (vowels, consonants, others)
}
//接受函数
let total=count("Alex is 15 Day")

println("元音："+String(total.vowels)+" "+"辅音字母："+String(total.consonants)+" 其他："+String(total.others))

//var s1,s2,s3:Int=count("")  这种方式go中是可以的，Swift 是不行的
//可以用这种方式接受
let (s1,s2,s3)=count("I'm a Chinese!")

println(s1)

```
>Swift 的多返回值，本质上就是一个元组类型，而不像 Golang 一样个可以直接通过多个变量直接接受 

**参数命名** 

参数命名：就是对函数的参数给一个明确的变量。这个在其他语言中似乎是一个默认的方式，书写时也就理所当然。 

```
func someFunction(parameterName: Int){
	//parameterName 就是对参数的命名，而在其他语言中直接说参数名
}
//也可以这样，不对参数命名
func test(Int){
    println("测试")
}
test(2) //真没有发现这样，到底有什么用
```
**外部参数名称** 

当调用函数，想知道参数明确的意图时，对参数命名是很有用的。如果你希望用户函数提供参数名称调用你的函数时,为每个参数命名。除了参数名称外，在它所支持的类型参数名称之前写一个外部参数名称,之间用一个空格来分隔，这就是Swift的**外部参数名称**。

>如果为函数提供了外部参数名称，必须在函数调用的时使用(否则会出现编译错误)。 

```
//定义一个函数，externalParameterName命名参数
 func someFunction(externalParameterName localParameterName: Int) {
   println(localParameterName)
}

someFunction(externalParameterName:34) //调用
```
比如定义一个join函数用于字符串链接，s1和s2两个字符串，joiner表示链接符  

```
func join(s1: String, s2: String, joiner: String) -> String {
    return s1 + joiner + s2
}
```

为了明确函数的各个参数的意图。为每个参数一个外部命名。

```
func join(string s1: String, toString s2: String, withJoiner joiner: String)
    -> String {
        return s1 + joiner + s2
}
``` 
对于`join`函数，前两个参数仅仅是表面字符类型，当然可以选择不对其外部命名

```
func join( s1: String, toString s2: String, withJoiner joiner: String)
    -> String {
        return s1 + joiner + s2
}

println(join("hello",toString:"World",withJoiner:"-"))
//强调，对外部命名的参数，必须在调用时使用
``` 
对参数的外部命名时，函数的参数的本地命名可以直接利用是，没有必要直接写两次，可以通过`#`简写。

```
func containsCharacter(#string: String, #characterToFind: Character) -> Bool {
    for character in string {
        if character == characterToFind {
            return true
        }
    }
    return false
}

let containsAVee = containsCharacter(string: "aardvark", characterToFind: "v")
```
**默认参数** 
可以给函数的参数，设置一个默认值，在函数调用时，可以忽略拥有默认值的参数。

``` 
//对连接字符串设置一个默认值
func join( s1: String, toString s2: String, withJoiner joiner: String=",")
    -> String {
        return s1 + joiner + s2
}

println(join("hello",toString:"World",withJoiner:"-"))
//使用默认的连接符
println(join("你好",toString:"世界"))
```
**可变参数**  


