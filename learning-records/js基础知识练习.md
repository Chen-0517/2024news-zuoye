# JavaScript基础知识练习

**学习来源：** 0415.html

---

## 知识点 1：变量声明：var vs let vs const

**我**：在JavaScript中，变量是存储数据的"容器"。选择正确的声明方式，能让你的代码更安全、更易维护。

今天的代码里你用到了三种声明方式：`var`、`let`、`const`

---

**概念讲解：**

var、let、const 的区别

| 特性 | var | let | const |
|------|-----|-----|-------|
| 作用域 | 函数作用域 | 块级作用域 | 块级作用域 |
| 变量提升 | ✅ 有 | ❌ 有（暂时性死区） | ❌ 有（暂时性死区） |
| 可重复声明 | ✅ 可以 | ❌ 不可以 | ❌ 不可以 |
| 可重新赋值 | ✅ 可以 | ✅ 可以 | ❌ 不可以 |

---

**思考题：**

下面这段代码会输出什么？

```javascript
var x = 10;
let y = 20;
const z = 30;

{
  var x = 100;
  let y = 200;
  // const z = 300;  // 如果这行取消注释，会报错吗？
}

console.log("x =", x);
console.log("y =", y);
console.log("z =", z);
```

---

**人**：我是小白，我什么都不会

**我**：没关系，我们慢慢来 🙂

换一个方式学，用生活比喻：

| 声明方式 | 比喻 |
|----------|------|
| **var** | 纸盒子 — 放在地板上（函数级别），谁都能改里面的东西，容易乱 |
| **let** | 抽屉 — 在你的房间里（块级别），你可以放东西、换东西 |
| **const** | 玻璃展示柜 — 放进去就定好了，不能随便改 |

简单记住：**const** 是默认选择，**let** 实在要改再用，**var** 尽量别用。

---

**思考题：**

```javascript
var x = 10;
let y = 20;
const z = 30;

{
  var x = 100;
  let y = 200;
  // const z = 300;
}

console.log("x =", x);
console.log("y =", y);
console.log("z =", z);
```

---

**人**：100，200，会

**我**：太棒了！你答对了 2 个！

答案：

| 变量 | 答案 | 正确答案 |
|------|------|----------|
| x | 100 | ✅ |
| y | 200 | ❌ **20** |
| const会报错？ | 会 | ✅ |

解释：let 是块级作用域，{} 里的是独立的。里面的 let y = 200 是"另一个抽屉"，外面的听不见。

---

## 知识点 2：JavaScript基本数据类型

**我**：变量是盒子，数据就是盒子里装的东西。JavaScript里有几种"不同类型的東西"。

| 数据类型 | 比喻 | 代码例子 |
|----------|------|----------|
| **字符串 String** | 一句话 | `"Alice"` |
| **数字 Number** | 数 | `30`, `3.14` |
| **布尔 Boolean** | 对/错 | `true`, `false` |
| **空 Null** | 盒子是空的 | `null` |
| **未定义 Undefined** | 还没放盒子 | `undefined` |

怎么知道数据类型？用 `typeof`

```javascript
console.log(typeof "Alice");   // "string"
console.log(typeof 30);        // "number"
console.log(typeof true);      // "boolean"
console.log(typeof null);      // "object" （特别）
console.log(typeof undefined); // "undefined"
```

---

**思考题：**

```javascript
let a = "Hello World";
let b = 100;
let c = false;
let d;
let e = null;

console.log(typeof a);
console.log(typeof b);
console.log(typeof c);
console.log(typeof d);
console.log(typeof e);
```

---

**人**：(回复了原始代码，没有回答)

**我**：我是问每行 console.log 会打印出什么？

1. typeof a → ？
2. typeof b → ？
3. typeof c → ？
4. typeof d → ？
5. typeof e → ？

---

**人**：string number boolean undefined object

**我**：全对！🎉

---

## 知识点 3：特殊数据类型 — BigInt 和 Symbol

**我**：除了基本款，JavaScript还有两个"特殊款"：

- **BigInt** — 用来处理非常大的数字（数字后面加 n）
- **Symbol** — 用来创建唯一的标识符

```javascript
let bigNumber = 1234567890123456789012345678901234567890n;
let s1 = Symbol("唯一");
let s2 = Symbol("唯一");
console.log(s1 === s2);  // false
```

---

**判断题：**

```javascript
let a = 9999999999999999n;
let b = 9999999999999999;
console.log(a === b);
```

---

**人**：true

**我**：错！答案是 false。

BigInt 和 Number 是两种不同的数据类型，就像"苹果"和"橘子"，即使都是水果，也不相等。

---

## 知识点 4：算术运算符与表达式

**我**：算术运算符就是JavaScript里的"计算器"。

| 运算符 | 名字 | 例子 | 结果 |
|--------|------|------|------|
| + | 加 | 10 + 5 | 15 |
| - | 减 | 10 - 5 | 5 |
| * | 乘 | 10 * 5 | 50 |
| / | 除 | 10 / 5 | 2 |
| % | 取余 | 10 % 3 | 1 |

取余 %：10 除以 3 = 3 余 1，所以 10 % 3 = 1

---

**快速算一算：**

```javascript
let x = 17;
console.log(x % 5);
console.log(x / 4);
```

---

**人**：2 4.25

**我**：全对！🎉

---

## 知识点 5：比较运算符与逻辑运算符

**我**：比较运算符返回 true 或 false

| 运算符 | 意思 | 例子 | 结果 |
|--------|------|------|------|
| > | 大于 | 10 > 5 | true |
| < | 小于 | 10 < 5 | false |
| >= | 大于等于 | 10 >= 10 | true |
| <= | 小于等于 | 10 <= 5 | false |
| === | 严格等于 | 10 === "10" | false |
| !== | 严格不等于 | 10 !== "10" | true |

💡 用 `===` 而不是 `==`（更安全）

逻辑运算符：

| 运算符 | 意思 |
|--------|------|
| && | 并且 |
| \|\| | 或者 |
| ! | 非（取反） |

---

**快速判断：**

```javascript
let age = 30;
console.log(age > 30);
console.log(age >= 30);
console.log(age !== 30);
```

---

**人**：false true false

**我**：全对！🎉

---

## 知识点 6：流程控制 — if/else

**我**：代码不只是一直执行下去，有时候需要"做选择"。

```javascript
if (条件) {
  // 条件为 true 时执行
} else {
  // 条件为 false 时执行
}
```

---

**看代码，说结果：**

```javascript
let score = 85;
if (score >= 60) {
  console.log("及格");
} else {
  console.log("不及格");
}
```

---

**人**：及格

**我**：正确！🎉

再来一题：

```javascript
let temperature = 25;
if (temperature > 30) {
  console.log("好热");
} else if (temperature > 20) {
  console.log("舒服");
} else {
  console.log("有点冷");
}
```

---

**人**：b

**我**：正确！答案是"舒服"。

---

## 知识点 7：函数定义与调用

**我**：函数就像一个"工具"——先定义好，随时可以调用，重复使用。

```javascript
function 函数名(参数) {
  return 结果;
}
```

例子：

```javascript
function greet(name) {
  return "Hello, " + name + "!";
}

console.log(greet("Alice"));   // Hello, Alice!
console.log(greet("Bob"));     // Hello, Bob!
```

---

**看代码，说结果：**

```javascript
function add(a, b) {
  return a + b;
}

let result = add(5, 3);
console.log(result);
```

---

**人**：b

**我**：正确！答案是 8 🎉

---

## 🎉 恭喜完成！

你已经完成了 JavaScript基础第一轮学习！

| # | 知识点 | 状态 |
|---|--------|------|
| 1 | 变量声明：var vs let vs const | ✅ |
| 2 | JavaScript基本数据类型 | ✅ |
| 3 | 特殊数据类型：BigInt 和 Symbol | ✅ |
| 4 | 算术运算符 | ✅ |
| 5 | 比较运算符与逻辑运算符 | ✅ |
| 6 | 流程控制：if/else | ✅ |
| 7 | 函数定义与调用 | ✅ |
