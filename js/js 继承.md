# js 组合继承
!['object prototype'](http://www.mollypages.org/tutorials/jsobj_full.jpg)  

``` javascript
function Parent(sName) {
	this.name = sName;
	this.color = []
}
Parent.prototype.show = function() {
	console.log("Parent: " + this.name)
}

function Child(sName) {
	// call()和apply()都可以
	Parent.call(this, sName)
}

Child.prototype = new Parent();
//与以上Child.prototype = new Parent()的区别?
// Child.prototype = Object.create(Parent.prototype);

// Object.create = function( proto ) {
//     function f(){}
//     f.prototype = proto;
//     return new f;
// };

Child.prototype.constructor = Child;

```

* Parent.call(this, sName); 可以使Child继承Parent的属性和方法,Child每个实例的各自属性，互不干扰。可以传参数给Parent。但是，Child实例后，再向Parant.prototype添加一个方法say()，或是属性，这个Child实例是不能访问Parent的say()方法，或是属性。

``` javascript
var child = new Child('Jun');

Parent.prototype.say = function() {
	console.log("My name: " + this.name)
}
//当调用child.say(),会报错:child.say is not a function
child.say();
```

* Child.prototype = new Parent(); 通过原型链，Child继承Parent的属性和方法。Parent.prototype添加属性和方法，Child实例都可以访问。但是，Child.prototype.constructor指定向Parent的构造函数。

# js 寄生组合式继承

``` javascript
// 继承函数
function extend(subClass,superClass){
	var F = function () {};
	F.prototype = superClass.prototype;
	subClass.prototype = new F();
	subClass.prototype.constructor = subClass;
}

function Parent(sName) {
	this.name = sName;
}
Parent.prototype.show = function() {
	console.log("Parent: " + this.name);
}

function Child(sName) {
	// call()和apply()都可以
	Parent.call(this, sName);
}

extend(Child,Parent);

var child = new Child('Jun');

child.show();

```
