<p><div class="toc">
<ul>
<li><a href="#javascipt-學習筆記">Javascipt 學習筆記</a><ul>
<li><a href="#文詞對照">文詞對照</a></li>
<li><a href="#overview">Overview</a></li>
<li><a href="#class-類別">Class 類別</a></li>
<li><a href="#object-物件-類別的實體">Object 物件 (類別的實體)</a></li>
<li><a href="#物件的產生方式">物件的產生方式</a><ul>
<li><a href="#實字模式範例">實字模式範例</a></li>
<li><a href="#關鍵字new範例">關鍵字new範例</a></li>
<li><a href="#建構式範例">建構式範例</a></li>
<li><a href="#函數範例">函數範例</a></li>
</ul>
</li>
<li><a href="#property-屬性">Property 屬性</a></li>
<li><a href="#method-方法">Method 方法</a></li>
</ul>
</li>
</ul>
</div>
</p>



<h1 id="javascipt-學習筆記">Javascipt 學習筆記</h1>

<blockquote>
  <p>Written with <a href="https://stackedit.io/">StackEdit</a> <br>
  這裡記錄了我學習<code>Javascript</code>的心得</p>
</blockquote>



<h2 id="文詞對照">文詞對照</h2>

<ol>
<li>Object = 物件，類別的實體化</li>
<li>Type = 型別</li>
<li>Function = 函式</li>
<li>Function Scope = 函式作用域</li>
<li>Class = 類別，用來定義物件的特性，像是行為以及屬性</li>
<li>Method = 方法，描述物件的行為</li>
<li>Constructor = 建構式，在物件被實體化的過程當中會被呼叫的方法，命名通常與類別名稱一致</li>
<li>Property = 物件的屬性值</li>
<li>Object Literal = 「實字模式」或「物件實體語法」，用大括弧<code>{}</code>符號產生物件的方式</li>
</ol>

<h2 id="overview">Overview</h2>

<p>Javascript 是一種動態物件導向的語言，它有著類別、運算子、標準內嵌的物件以及方法。Javascript 的語法源自於 Java 及 C 語言，所以你會發現在 Javascript 也看的到類似的結構，但與其他語言不同的一個關鍵就是 Javascript 本身沒有<strong>類別</strong>的概念。其他主要的差別有：</p>

<ul>
<li>函式即是物件</li>
<li>函式裡可放置執行程式，並且指派給其他物件</li>
</ul>



<h2 id="class-類別">Class 類別</h2>

<p>在 Javascript 裡面沒有用來宣告類別的語法，但我們可以透過函數來定義類別。在下面的範例裡面，我們使用函數建立一個名為 <strong>Person</strong> 的類別，而這個類別的建構式是一個空的函數：</p>

<pre><code>var Person = function () {};
</code></pre>

<p>除了透過函數建立類別的方法外，後面的篇幅會介紹其他產生類別實體的方式。</p>

<blockquote>
  <p><strong>注意：</strong> <code>Person</code>這個變數背後指向一個空的函數，且在被實體化之前，變數的型別會是 Function。</p>
</blockquote>



<h2 id="object-物件-類別的實體">Object 物件 (類別的實體)</h2>

<p>有了 Person 類別後，接著我們要使用<code>new</code>這個關鍵字針對 Person 類別做「實體化」的動作，來產生 person1 、 person2 兩個物件：</p>

<pre><code>var person1 = new Person();
var person2 = new Person();
</code></pre>

<p><code>new</code>語法會產生一個使用者自訂型別或任何一個有建構式函數的 Javascript 內嵌物件型別的<strong>實體</strong>。</p>

<p>在「實體化」的動作裡，建構式會被呼叫，如果我們需要產生或是初始化物件的屬性值時，就可以在建構式裡面處理。而實體化後，變數<code>person1</code>存放的物件型別就是 object ，我們可以透過<code>console.log(typeof person1);</code>的輸出結果得知。</p>



<h2 id="function-scope-函數作用域">Function Scope 函數作用域</h2>

<p>在Javascript裡面定義變數時，可以依照變數擺放的位置來決定該變數是全域變數或是局部變數。當我們將宣告的變數放置在函數內，這時我們稱其為區域變數。區域變數的生命週期會隨著函數的結束而消失，區域變數被存取的範圍僅限於該函數本身，此時我們稱該範圍為函數作用域。</p>

<p>當宣告的變數放在函數外時會被視為全域變數，全域變數的生命週期會隨著整個程式結束才消失，而且在任一函數內都可存取全域變數的值。</p>

<pre><code>var x = 1;

function Add (y) {
    x = x + 1;
    var result = x + y;
    return result;
};

console.log(Add(3)); // logs "5"
console.log(x);      // logs "2"
console.log(y);      // logs "ReferenceError: y is not defined"
</code></pre>

<h2 id="物件的產生方式">物件的產生方式</h2>

<p>產生物件的主要方式列表如下：</p>

<ol>
<li>實字模式</li>
<li>關鍵字<code>new</code> </li>
<li>建構式</li>
<li>函數</li>
</ol>



<h3 id="實字模式範例">實字模式範例</h3>

<p>透過大括弧<code>{}</code>符號產生物件的方式。大括弧內的<code>this</code>指的是 person 物件自己本身。</p>

<pre><code>var Person = {
    firstName: 'John',             // 定義第一個屬性
    lastName: 'Smith',             // 定義第二個屬性
    getFullName: function() {      // 定義一個方法
        return this.firstName + ' ' + this.lastName;
    }
};

// logs "John Smith"
console.log(Person.getFullName());
</code></pre>

<h3 id="關鍵字new範例">關鍵字<code>new</code>範例</h3>

<p>使用<code>new Object()</code>語法建立一個物件，接著指派給<code>person</code>變數。</p>

<pre><code>var Person = new Object();            // 建立一個空的物件
Person.firstName = "John";            // 定義第一個屬性
Person.lastName = "Smith";            // 定義第二個屬性

Person.getFullName = function () {    // 定義一個方法
    return Person.firstName + ' ' + Person.lastName;
};

// logs "John Smith"
console.log(Person.getFullName());
</code></pre>

<h3 id="建構式範例">建構式範例</h3>

<p>判斷是否為透過建構式產生物件，可透過觀察<strong>context</strong>端有無出現<code>new</code>的關鍵字得知。</p>

<pre><code>var Person = function(_firstName, _lastName) {
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
</code></pre>

<blockquote>
  <p><strong>注意：</strong> <code>Person.firstName</code>會輸出”undefined”的原因，是因為<code>Person</code>是型別，透過<code>new</code>實體化產生物件後，才能使用建構式裡定義好的屬性與方法。 </p>
</blockquote>



<h3 id="函數範例">函數範例</h3>

<p>函數範例與建構式範例不同的地方在於：</p>

<ul>
<li>建構式範例透過<code>this</code>定義 context 端可以使用的屬性與方法</li>
<li>函數範例透過<code>return</code>定義了 Key-Value pair ，包含了可以讓 context 端使用的屬性與方法</li>
<li>函數不需透過<code>new</code>產生物件即可讓 context 端使用</li>
</ul>

<p>範例如下：</p>

<pre><code>var Person = function(firstName, lastName) {
    return {
        "firstName": firstName,
        "lastName": lastName,
        "getFullName": function() {
            return firstName + ' ' + lastName;
        }
    };
};

// logs "John Smith"
var instance = Person('John','Smith');
console.log(instance.getFullName());
</code></pre>

<h2 id="property-屬性">Property 屬性</h2>

<p>屬性是存放在類別裡的變數，每一個類別實體化後產生的物件都會有定義好的屬性，而且屬性的預設值可以透過類別的建構式裡面設定。那我們如何在物件裡面存取該類別的屬性呢？這時候可以透過<code>this.Property</code>這個語法，取得或設定這個屬性的值：</p>

<pre><code>var Person = function (firstName) {
  this.firstName = firstName;
  console.log('Person instantiated');
};

var person1 = new Person('Alice');
var person2 = new Person('Bob');

// Show the firstName properties of the objects
console.log('person1 is ' + person1.firstName); // logs "person1 is Alice"
console.log('person2 is ' + person2.firstName); // logs "person2 is Bob"
</code></pre>



<h2 id="method-方法">Method 方法</h2>

<p>我們透過類別上定義好的方法，來決定這個類別會有那些抽象行為。那我們如何定義方法的具體行為呢？這時候可以透過指派函數給方法。拿我們之前使用的<code>Person</code>範例來說，我們想替這個類別增加一個<code>sayHello()</code>的方法，這時候我們可以透<code>this</code>這個關鍵字，然後定義一個<code>sayHello</code>屬性，在等號右邊的<code>function()</code>寫法表示我們將函數指定給<code>sayHello</code>屬性，例如<code>this.sayHello = 函數</code>，接著我們就可以在函數裡面實作方法內容了。</p>

<pre><code>var Person = function (firstName) {
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
</code></pre>