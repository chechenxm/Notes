# jQuery 学习笔记

## jQuery是什么？

jQuery 是一个轻量的 js 库，jQuery 可以让 js 代码写起来更容易。

jQuery 支持 HTML/Dom操作、CSS操作、Ajax

## jQuery基本语法

`$(Selector).action()`

* $ 符号 定义访问 jQuery 的元素

* selector 选择器，用来查找HTML元素
* action() 对元素执行的jQuery操作
* 

**文档加载**

```js
$(function(){
	// jQuery methods go here...
});
//另一种方法
$(document).ready(function(){

  // jQuery methods go here...

});
```

这可以防止在文档加载完成之前运行任何jQuery代码（准备就绪），可以将 js 代码放在文档正文之前。

可能会失败的情况：

1. 隐藏尚未加载出的元素

2. 试图获取尚未加载出来的元素高度与宽度

### 选择器

* 基本选择器

```js
//多个参数以逗号分隔 $("arg1,arg2,......")

$("tag_name") //标签选择器

$(".class_name") //class

$("#id_name")//id
```
* 属性选择器

  ```js
  $("[href]") //含有 href 属性的元素
  
  $("[href = 'xx.html']") // href="xx.html"的元素
  
  $("[href != 'xx.html']")
  
  $("[title ^=  'hello']") //以“hello”开头
  
  $("[href $= '.txt']") //以 “.txt” 结尾
  
  $("[title ~=  'hello']") //含有
  
  $(""[title |=  'hello']"") 等于 或 含有且其后有连字符
  ```

  

* 按顺序的选择器

  ```js
  $("p:first") // 第一个 p 元素
  
  $("p:last") // 最后一个 p 元素
  
  $("p:even") // 第偶数个 p 元素
  
  $("p:odd") // 第奇数个 p 元素 
  ```
  
* 子元素顺序选择器

  ```js
  $("p:first-child") // 是父元素第一个子元素的 p 元素
  
  $("p:last-child")
  
  $("p:first-of-type") // 是父元素第一个 p 元素的 p 元素
  
  $("p:last-of-type")
  
  $("p:nth-child(2)") // 是父元素中第二个子元素的 p 元素（从 1 开始）
  
  $("p:nth-last-child(2)") // 是父元素中倒数第二个子元素的 p 元素
  
  $("p:nth-of-type(2)") //是父元素的所有子元素p中排第二的 p 元素
  
  $("p:nth-last-of-type(2)")
  
  $("p:only-child") // 所有是父元素中唯一子元素的 p 元素
  
  $("p:only-of-type") // 所有是父元素中唯一是 p 元素的 p 元素
  ```

* 符号选择器

  ```js
  $("div > p") // 所有是 div 元素的直接子元素的 p 元素
  
  $("div p") // 所有事 div 子元素的 p 元素
  
  $("div + p") // 所有是 div 下一个元素的 p 元素
  
  $("div ~ p") // 所有是 div 同胞节点的 p 元素
  ```

* 列表内的选择器

  ```js
  $("ul li:eq(3)")// The fourth element in a list (index starts at 0)
  
  $("ul li:gt(3)")// List elements with an index greater than 3
  
  ("ul li:lt(3)")// List elements with an index less than 3
  
  $("input:not(:empty)")// All input elements that are not empty
  ```
  
* 关键字选择器

  ```js
  $(":header")//	All header elements <h1>, <h2> ...
  $(":animated")//	All animated elements
  $(":focus")//	The element that currently has focus
  $(":contains('Hello')")	// All elements which contains the text "Hello"
  $("div:has(p)")//	All <div> elements that have a <p> element
  $(":empty")//	All elements that are empty
  $(":parent")//	All elements that are a parent of another element
  $("p:hidden")//	All hidden <p> elements
  $("table:visible")//	All visible tables
  $(":root")//	The document's root element
  $("p:lang(de)")//	All <p> elements with a lang attribute value starting with "de"
  ```
  
* 表单中的`<input>`选择器

  ```js
  $(":input")//	All input elements
  $(":text")//	All input elements with type="text"
  $(":password")//	All input elements with type="password"
  $(":radio")//	All input elements with type="radio"
  $(":checkbox")//	All input elements with type="checkbox"
  $(":submit")//	All input elements with type="submit"
  $(":reset")//	All input elements with type="reset"
  $(":button")//	All input elements with type="button"
  $(":image")//	All input elements with type="image"
  $(":file")//	All input elements with type="file"
  $(":enabled")//	All enabled input elements
  $(":disabled")//	All disabled input elements
  $(":selected")//	All selected input elements
  :$(":checked")//	All checked input elements
  ```
## jQuery 事件

| **Mouse Events** | **Keyboard Events** | **Form Events** | **Document/Window Events** |
| ------------ | :----------- | ------------ | ------------ |
| click |	keypress |	submit |	load |
| dblclick |	keydown	| change |	resize |
| mouseenter |	keyup |	focus |	scroll |
| mouseleave	| 	blur |    |	unload |

* **` on() ` 方法**

  该`on()`方法为所选元素附加一个或多个事件处理程序。

  ```js
  $("p").on({
    mouseenter: function(){
      $(this).css("background-color", "lightgray");
    },
    mouseleave: function(){
      $(this).css("background-color", "lightblue");
    },
    click: function(){
      $(this).css("background-color", "yellow");
    }
  });
  ```

## jQuery 对 HTML/CSS 操作

* 获取内容

  ```js
  $("p").text //
  
  $("input['text']").val()// 获取表单内容
  ```

  