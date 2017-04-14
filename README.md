# reference-type （js中的引用类型）
  
    var num1; //这个时候不进行内存分配
    var num3=9;//分配内存
    var num4=num3;//会不会分配？
    
- 变量中的引用类型
> 答案是会分配类型。

    num3=3333333;
    num4=4444444;
    console.log(num3)
    console.log(num4) 
    //当更改数据，值不一样的本质是这里分配两个空间独立存储
- 字符型
        
       //字符串
        var str1; //这个时候不进行内存分配
        var str2 = 'zzc'; //分配内存
        var str3=str2; //问题，分配内存?
        //分配

- 数组
    
        var arr1=['zzc','ccz'];//arr1分配内存
        //引用类型其实是指向同一个地址,也就是操纵的其实是同一个位置
        var arr2=arr1;   //问题：这里arr2会不会分配内存
        console.log(arr1[0]);
        console.log(arr2[0]);
> 答案是不会给arr2，分配内存地址。
- 函数
  
  
      function sum(num1,num2)
      {
        return num1 + num2;
      }
      console.log(sum(10,10)); //20
      var anotherSum = sum;
> 答案同数组
- 对象
  
      function product(){

      }
      var pro1 = new Product();
      var pro2 = new Product();
> 答案同数组、函数
## 原因
- 变量和字符串都会创建自己的内存空间，var a = b；相当于给a，和b都分别创建了一个内存。
- 数组，函数，对象则是复制内存地址，地址指向真正的内存空间（指针）。
## 总结
    
        function show(x) {
        console.log(typeof(x));    // undefined 值类型
        console.log(typeof(10));   // number 值类型
        console.log(typeof('abc')); // string 值类型
        console.log(typeof(true));  // Boolean 值类型
        
        console.log(typeof(function () { }));  //函数 引用类型
        console.log(typeof([1, 'a', true]));  //数组  引用类型
        console.log(typeof ({ a: 10, b: 20 }));  //object 或者json  引用类型
        console.log(typeof (null));  //null  引用类型
        console.log(typeof (new Number(10)));  //内置对象 引用类型
    }
    show();
- 其中上面的四种（undefined, number, string, boolean）属于值类型，不是对象。
- 函数、数组、对象、null、new Number(10)都是对象。他们都是引用类型。
- 在最新语法中，null和undefined已经合并了。
## 面试题
### 01
      var a = {"x": 1};
      var b = a;
      a.x = 2;
      console.log(b.x);
> 结果是？
### 02
      var a = {"x": 1};
      var b = a;
      a.x = 2;
      console.log(b.x);
      a = {"x":3};
      console.log(b.x);
- 答案：
* 第一题 2
* 第二题 2
- 解析：
* 第一题，json对象是引用类型，所以a.x更改了真实内存的值,b指向该内存地址。
* 第二题，a是创建了一个新的对象,所以它指向原来的指针断了，而b仍然指向原地址。


## 补充
- 内存分两种：栈内存，堆内存。
1. 栈内存只能保存单个单个的值。
2. 堆内存可以保存多个值。
> 所以，值类型和引用型就可以很好区分了
- 值类型都是保存在栈内存中，引用类型将内存地址保存在栈内存。（和数组的获取方式类似）
- 引用类型的数据会保存在堆内存。
           
       var p = new Product();
> 那么p就是在栈内存，真正的对象里面属性什么的都在堆内存。
