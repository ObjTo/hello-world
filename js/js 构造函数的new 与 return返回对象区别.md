假设构造函数Car用 `new` 运算符创建对象，构造函数中又有 `return`返回值时，需要注意返回的对象类型

- 当return返回值是基本类型(number, boolean, string, null, undefined)时, 则返回Car对象
- 当return返回值是引用类型(Object, Array, Function)时，则返回对应引用类型  

``` javascript
  function Car() {
    this.color = "blue";
    this.doors = 4;
    this.mpg = 25;
    this.showColor = function() {
        document.write(this.color);
    };

  // return;
  // return null;
  // return this;
  // return false;
  // return 'hello world';
  // return 2;

  // return {};                            // 返回 {}
  // return [];                            // 返回 []
  // return function(){};                  // 返回 function

}

```
