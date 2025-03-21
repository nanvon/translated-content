---
title: RegExp.rightContext ($')
slug: Web/JavaScript/Reference/Global_Objects/RegExp/rightContext
---
{{JSRef}} {{non-standard_header}}

**rightContext** 非标准属性是正则表达式的静态和只读属性，含有最新匹配的右侧子串。 `RegExp.$'` 是这个属性的别名。

## 语法

```plain
RegExp.rightContext
RegExp["$'"]
```

## 描述

`rightContext` 属性是静态的，不是正则表达式独立对象的属性。反之，你应始终将其使用为 `RegExp.rightContext` 或者 `RegExp["$'"]`。

`rightContext` 属性的值是只读的，并且会在匹配成功时修改。

你不能使用属性访问器 (`RegExp.$'`) 来使用简写的别名，因为解析器在这里会将其看做字符串的开始，并抛出 {{jsxref("SyntaxError")}}。使用 [方括号符号](/zh-CN/docs/Web/JavaScript/Reference/Operators/Property_Accessors)来访问属性。

## 示例

### 使用 `rightContext` 和 `$'`

```js
var re = /hello/g;
re.test('hello world!');
RegExp.rightContext; // " world!"
RegExp["$'"];       // " world!"
```

## 规范

非标准。并不是任何现行规范的一部分。

## 浏览器兼容性

{{Compat}}

## 另见

- {{non-standard_inline}} {{jsxref("RegExp.input", "RegExp.input ($_)")}}
- {{non-standard_inline}} {{jsxref("RegExp.lastMatch", "RegExp.lastMatch ($&amp;)")}}
- {{non-standard_inline}} {{jsxref("RegExp.lastParen", "RegExp.lastParen ($+)")}}
- {{non-standard_inline}} {{jsxref("RegExp.leftContext", "RegExp.leftContext ($`)")}}
- {{non-standard_inline}} {{jsxref("RegExp.n", "RegExp.$1-$9")}}
