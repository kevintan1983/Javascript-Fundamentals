[TOC]

# Javascipt 學習筆記

> Written with [StackEdit](https://stackedit.io/)
> 這裡記錄了我學習`Javascript`的心得

## 文詞對照
1. Object = 物件，類別的實體化
2. Type = 型別
3. Function = 函式
4. Class = 類別，用來定義物件的特性，像是行為以及屬性
5. Method = 方法，描述物件的行為
6. Constructor = 建構式，在物件被實體化的過程當中會被呼叫的方法，命名通常與類別名稱一致
7. Property = 物件的屬性值
8. Object Literal = 「實字模式」或「物件實體語法」，用大括弧`{}`符號產生物件的方式

## Overview
Javascript 是一種動態物件導向的語言，它有著類別、運算子、標準內嵌的物件以及方法。Javascript 的語法源自於 Java 及 C 語言，所以你會發現在 Javascript 也看的到類似的結構，但與其他語言不同的一個關鍵就是 Javascript 本身沒有**類別**的概念。其他主要的差別有：

 - 函式即是物件
 - 函式裡可放置執行程式，並且指派給其他物件

## Class 類別
在 Javascript 裡面沒有用來宣告類別的語法，但我們可以透過函數來定義類別。在下面的範例裡面，我們使用函數建立一個名為 **Person** 的類別，而這個類別的建構式是一個空的函數：

	var Person = function () {};

除了透過函數建立類別的方法外，後面的篇幅會介紹其他產生類別實體的方式。
> **注意：** `Person`這個變數背後指向一個空的函數，且在被實體化之前，變數的型別會是 Function。

## Object 物件 (類別的實體)
有了 Person 類別後，接著我們要使用`new`這個關鍵字針對 Person 類別做「實體化」的動作，來產生 person1 、 person2 兩個物件：

	var person1 = new Person();
	var person2 = new Person();

`new`語法會產生一個使用者自訂型別或任何一個有建構式函數的 Javascript 內嵌物件型別的**實體**。

在「實體化」的動作裡，建構式會被呼叫，如果我們需要產生或是初始化物件的屬性值時，就可以在建構式裡面處理。而實體化後，變數`person1`存放的物件型別就是 object ，我們可以透過`console.log(typeof person1);`的輸出結果得知。

## 物件的產生方式
產生物件的主要方式列表如下：

1. 實字模式
2. 關鍵字`new` 
3. 建構式
4. 函數

### 實字模式範例
透過大括弧`{}`符號產生物件的方式。大括弧內的`this`指的是 person 物件自己本身。

	var person = {
		firstName: 'John',             // 定義第一個屬性
		lastName: 'Smith',             // 定義第二個屬性
		getFullName: function() {      // 定義一個方法
			return this.firstName + ' ' + this.lastName;
		}
	};

	// logs "John Smith"
	console.log(person.getFullName());

### 關鍵字`new`範例
使用`new Object()`語法建立一個物件，接著指派給`person`變數。

	var person = new Object();            // 建立一個空的物件
	person.firstName = "John";            // 定義第一個屬性
	person.lastName = "Smith";            // 定義第二個屬性
	
	person.getFullName = function () {    // 定義一個方法
		return person.firstName + ' ' + person.lastName;
	};
	
	// logs "John Smith"
	console.log(person.getFullName());

### 建構式範例
判斷是否為透過建構式產生物件，可透過觀察**context**端有無出現`new`的關鍵字得知。

	var Person = function(_firstName, _lastName) {
		this.firstName = _firstName;
		this.lastName = _lastName;
		this.getFullName = function() {
			return this.firstName + ' ' + this.lastName;
		};
	};
	
	var instance = new Person('John', 'Smith');
	
	// logs "John Smith"
	console.log(instance.getFullName());

	// logs "undefined"
	console.log(Person.firstName);
	console.log(Person.getFullName);

> **注意：** `Person.firstName`會輸出"undefined"的原因，是因為`Person`是型別，透過`new`實體化產生物件後，才能使用建構式裡定義好的屬性與方法。 

### 函數範例

## Property 屬性
屬性是存放在類別裡的變數，每一個類別實體化後產生的物件都會有定義好的屬性，而且屬性的預設值可以透過類別的建構式裡面設定。那我們如何在物件裡面存取該類別的屬性呢？這時候可以透過`this.Property`這個語法，取得或設定這個屬性的值：

	var Person = function (firstName) {
	  this.firstName = firstName;
	  console.log('Person instantiated');
	};

	var person1 = new Person('Alice');
	var person2 = new Person('Bob');

	// Show the firstName properties of the objects
	console.log('person1 is ' + person1.firstName); // logs "person1 is Alice"
	console.log('person2 is ' + person2.firstName); // logs "person2 is Bob"

## Method 方法
我們透過類別上定義好的方法，來決定這個類別會有那些抽象行為。那我們如何定義方法的具體行為呢？這時候可以透過指派函數給方法。拿我們之前使用的`Person`範例來說，我們想替這個類別增加一個`sayHello()`的方法，這時候我們可以透`this`這個關鍵字，然後定義一個`sayHello`屬性，在等號右邊的`function()`寫法表示我們將函數指定給`sayHello`屬性，例如`this.sayHello = 函數`，接著我們就可以在函數裡面實作方法內容了。

	var Person = function (firstName) {
	  this.firstName = firstName;
	  this.sayHello = function() {
	  	console.log("Hello, I'm " + this.firstName);
	  };
	};

	var person1 = new Person("Alice");
	var person2 = new Person("Bob");

	// call the Person sayHello method.
	person1.sayHello(); // logs "Hello, I'm Alice"
	person2.sayHello(); // logs "Hello, I'm Bob"





