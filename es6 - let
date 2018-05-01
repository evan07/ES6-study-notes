# ES6-study-notes
ES6 study notes
## let 
 // let 与 var
/* 一 */
    {
        let a = 12;
        var b = 10;
    }
    //console.log(a) // a is not defined
    //console.log(b) // b = 10
    // let 声明的变量只再其所在的代码块中有效的

/* 二 */
    // for 循环的计数器就很适合使用let 命令
    for (let i = 0; i < 10; i++) {
        // console.log(i) // 0,1,2,3,4,5,6,7,8,9
    }
    // console.log(i) // i is not defined -->原因：使用在for 循环里面使用let 定义的计数器 i ，只能在for循环体内有效，在循环体外面就会报错。

  var a = [];
   for(var i = 0; i < 10; i++){
       a[i] = function () {
           console.log(i)
       }
   }
   a[6] ();// 10,
    // 变量 i 是 var 声明的，在全局范围内都有效的，所以全局只有一个变量 i 。
    // 每一个循环，变量 i 的值都会发生改变，而循环内，被赋给数组 a 的函数内部的 console.log(i)中的 i 指向全局的 i.
    // 也就是说数组 a 的成员中的 i 指向的都是 同一个 i，导致运行时输出的是最后一轮的 i 的值，也就是10.
    // 也可以理解为，全局变量i的值在循环里是不断变化的，相当于全局变量 i不断的被声明和覆盖并赋值给 数组 a,

    // 如果使用 let ,声明的变量仅在块级作用域内有效，最后将输出 6
    var a = [];
    for(let i = 0; i < 10; i++){
        a[i] = function () {
            console.log(i);
        }
    }
    a[6] (); // 6
    // 上面的代码中，变量 i 是let声明的，当前的 i 只在本轮循环有效。所以每一次循环的 i，其实都是一个新的变量，于是最后输出的是 6 .
    // 大家可能会问，如果每一次循环的变量 i都是重新声明的，那么它怎么知道上一轮循环的值，从而计算出本轮循环的值呢？
    // 这是因为JavaScript引擎内部会记住上一轮循环的值，初始化本来的变量 i 时，就在上一轮循环的基础上进行计算。

    // 另外 for 循环还有一个特别之处，就是设置循环变量的那部分是一个父作用域，而循环体内部是一个单独的子作用域。
    for(let i = 0; i < 3; i++){
        let i = 'abc';
        console.log(i)
    }
    // 输出3次 abc
    // 这表明函数内部的变量 i 与循环变量 i 不在同一个作用域，而有各自单促的作用域。

/* 三 */  //不存在变量提升
    // var 命令发生 “变量提升” 现象，即变量可以在声明之前使用，值为 undefined。这种现象多多少少是有些奇怪的。
    // 按照一般的逻辑，变量应该在声明语句之后才可以使用的
    // 为了纠正这种现象，let命令改变了语法行为，它所声明的变量一定要在声明后使用，否则便会报错的

    // var 的情况
    console.log(foo) // undefined
    var foo = 2
    // 类似于 以下
    // var foo;// 变量被声明了。但是没有赋值，输出没有赋值的变量就是undefined;
    // console.log(foo)
    // foo = 2;// 在此处变量赋值

    // let 的情况
    // console.log(bar); // 报错
    // let bar = 2;
    /*
    在以上代码中，变量foo用var 命令声明会发生变量提升，即脚本开始运行时，变量foo便已经存在，但是没有值，所有会输出undefined 。
    变量bar 使用 let命令声明则不会发生变量提升。这表示在声明它之前，变量bar是不存在的，这时如果用到它，就会抛出一个错误。
    */

/* 四 暂时性死区 */
    var tmp = 123;
    if (true) {
        tmp = 'abc'; // ReferenceError 报错了
        // let tmp;
    }
    // 只要块级作用域内 存在 let 命令，它所声明的变量就“绑定（binding）”这个区域，不再受外部的影响。
    // 上面的代码中存在全局变量 tmp, 但是块级作用域内let 又声明了一个局部变量tmp,导致后者绑定这个块级作用域.
    // 所以在let声明变量前，对tmp赋值会报错的。
    // ES6明确规定，如果区块中存在 let 和 const 命令，则这个区块对这些命令声明的变量，从一开始就形成封闭作用域。只要在声明之前就使用这些变量。就会报错。
    // 总之，在代码块内，使用let命令声明变量之前。该变量都是不可用的。这在语法上称为“暂时性死区（temporal dead zone简称 TDZ）”.
    if (true) {
        // TDZ开始
        // tmp = 'abc' // ReferenceError
        // console.log(tmp); // // ReferenceError

        let tmp; // TDZ结束
        console.log(tmp); // undefined;
        tmp = 123
        console.log(tmp) //123
    }
    /*
    * 上面的代码中，在 let 命令声明变量 tmp 之前，都属于 变量 tmp的 “死区”
    * “暂时性死区” 也意味着 typeof 不再是一个百分之百安全的操作。
    *
    * */

    typeof x; // ReferenceError
    // let x;
    /*
    * 上面的代码中，变量x使用 let 命令声明，所以在声明之前都属于 x 的“死区”，只要用到该变量就会报错。
    * 因此，typeof 运行时就会抛出一个ReferenceError.
    * */
    // 如果一个变量根本没有被声明，使用typeof 反而不会报错。
    console.log(typeof undeclared_variable)  // undefined
    /*
    * 上面的代码中 变量undeclared_variable是不存在的变量。结果返回：undefined,
    * 所以在没有 let 之前，typeof 运算符是百分百安全的，永远不会报错。现在这一点不成立了
    * 这样的设计是为了让大家养成良好的编程习惯。变量一定要在声明之后使用。否则就会报错。
    * */

    // 有写 “死区” 比较隐蔽，不太容易发现的，如下：
    // function bar (x = y, y = 2) {
    //     return [x, y];
    // }
    //bar(); // 报错了
    /*
    * 上面的代码中，调用bar函数之所以报错（某些实现可能不报错），
    * 是因为参数 x 的默认值等于另一个参数 y ,而此时 y 还没有声明，属于 “死区”。
    * 如果 y 的默认值是 x,就不会报错。因为此时 x 已声明。
    * */
    function bar(x = 2, y = x) {
        return [x, y];
    }
    console.log(bar()); //[2, 2]

    // 下面的代码也会报错，与 var 的行为不同
    var x = x; // 不会报错
    // let y = y ; // 报错
    /*
    * 以上代码报错也是因为暂时性死区，使用let声明变量时，只要变量在还没有声明前使用的，就会报错。
    * 以上示例就属于这种情况，在变量 x 的声明语句还没有执行完成前就尝试获取 x 的值，导致出现“x未定义”的错误。
    * */

/* 五，不允许重复声明*/
    // let 不允许在相同作用域内重复声明同一个变量
    // 报错一
    function a() {
        let a  = 10;
        var a  = 1;
    }
    // a()
    // 报错二
    function a() {
        let a = 10;
        let a = 1;
    }
    // a()
    // 不能在函数内部重新声明参数
    function func (arg) {
        let arg;
    }
    // func()
    // 不报错
    function func (arg) {
        {
            let arg;
        }
    }
    func();

/*六 块级作用域*/
// ES5 只有全局作用域和函数作用域，没有块级作用域，这个导致很多场景不合理。
    // 第一种场景，内层变量可能会覆盖外层变量。
    var tmp =  new Date()
    function f() {
        // var tmp; // 内层的变量tmp声明提前了。导致内层的var tmp; 覆盖了外层的 tmp = new Date()
        console.log(tmp); // undefined
        if (false) {
            var tmp = 'Hello World'
        }
    }
    console.log(f()); // undefined

    // 第二种场景，用来计数的循环变量泄露为全局变量
    var s = 'hello';
    for(var i = 0; i < s.length; i++) {
        console.log(s[i]); // h e l l o
    }
    console.log(i); // 5
    /*
    * 上面的代码中，变量 i 只用来控制循环，但是循环结束后，它并没有消失，而是泄露成了全局变量。
     *  */

    // ES6 的 块级作用域
    // let 实际上为JavaScript新增了块级作用域
    function f1 () {
        // 外层
        let n = 5;
        if (true) {
            // 内层
            let n = 10;
        }
        // 外层代码块不受内层代码块的影响。
        console.log(n); //5; // 如果用 var 定义的话，输出的就是 10了。
    }
    f1();
    // ES6 允许块级作用域的任意嵌套 (外层作用域是无法读取内层作用域的变量的。)
    {{{{{let insane = "Hello World"}}}}}

    // 外层作用域是无法读取内层作用域的变量的
    {{{{
        {let insane = "Hello World"}
        // console.log(insane); // 报错的
    }}}}
    // 内层作用域可以定义外层作用域的同名变量的
    {{{{
        let insane = "Hello World"
        {let insane = "Hello World"}
    }}}}

    // ES5 规定，函数只能在顶级作用域或者函数作用域之中声明的，不能在块级作用域中声明。
    // 但是浏览器没有遵守这个规定，为了兼容以前的代码，还是支持在块级作用域之中声明函数。因此以下的情况都能运行，不会报错。
    // 情况一
    if (true) {
        function f () {
        }
    }
    // 情况二
    try {
        function f() {}
    } catch (e) {

    }

    // ES6 引入了块级作用域，明确允许在块级之中声明函数。
    // ES6 规定，在块级作用域之中，函数声明语句的行为类似于 let, 块级作用域之外不可引用。
    function f () {console.log('I am outside!');}
    (function () {
        if (false) {
            // 重复声明一次函数 f
            function f() {console.log('I am inside!');}
        }
        // f();
    }())
    // 在ES6 中会报错
    // 应该避免在块级作用域内声明函数。如果确实需要，也应该写成函数表达式得形式。而不是函数声明语句

    // 函数声明语句
    {
        let a = 'secret'
        function f() {
            return a
        }
    }

    // 函数表达式
    {
        let a = 'secret';
        let f = function () {
            return a ;
        }
    }

    // do表达式
    // 本质上，块级作用域是一个语句，将多个操作封装再一起，没有返回值。
    // 现在有个提案，使得块级作用域可以变为表达式，即可以返回值，办法就是再块级作用域之前加上 do.使他变为 do表达式。
    // let x = do {
    //     let t = f();
    //     t * t + 1;
    // }
    // console.log(x)
