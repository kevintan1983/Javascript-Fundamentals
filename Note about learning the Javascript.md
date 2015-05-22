<p><div class="toc">
<ul>
<li><a href="#javascipt-學習筆記">Javascipt 學習筆記</a><ul>
<li><a href="#文詞對照">文詞對照</a></li>
<li><a href="#overview">Overview</a></li>
<li><a href="#class-類別">Class 類別</a></li>
<li><a href="#object-物件-類別的實體">Object 物件 (類別的實體)</a></li>
<li><a href="#function-scope-函數作用域">Function Scope 函數作用域</a></li>
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
<li><a href="#nodejs-學習心得">Node.js 學習心得</a><ul>
<li><a href="#event-loop1">Event Loop1</a></li>
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



<h1 id="nodejs-學習心得">Node.js 學習心得</h1>

<p>Node.js 是一套以非同步、事件驅動設計為主的套件，同時也適合用來建置高擴展性的網站程式。我們從這個 “hello world” 的範例裡面可以清楚瞭解到 Node.js 可以同時處理許多 HTTP 連線，每當有新連線時，會觸發 callback 事件處理每個 request ，當沒有連線時，Node.js 則是呈現休眠狀態。</p>

<pre><code>var http = require('http');

http.createServer(function (req, res)) {
    res.writeHead(200, {Content-Type': 'text/plain'});
    res.end('Hello World\n');
}).listen(3000, "127.0.0.1");

console.log('Server running at http://127.0.0.1:3000/');
</code></pre>

<p>這個範例顯示出 Node.js 與其他技術使用多執行緒處理 request 差別的地方。相較來說，以多執行緒為基礎的方式處理 request 除了效率較低之外還需要煩惱 process 資源被鎖住的問題。</p>



<h2 id="event-loop">Event Loop</h2>

<p>Node.js 的平行處理模式是透過 <strong>event loop</strong><a href="#fn:eventloop" id="fnref:eventloop" title="See footnote" class="footnote">1</a> 的機制來處理。在解釋 event loop 之前，我們先透過下圖釐清 Javasript 在執行時期，Stack、Heap、Queue在系統中扮演的腳色與作用。</p>

<p><img src="https://developer.mozilla.org/files/4617/default.svg" alt="Event Loop" title=""></p>

<p><strong>Stack 堆疊</strong> <br>
函式在被呼叫時，都會在 Stack 裡產生一個記憶體區塊，並且是以後進先出(LIFO)的順序被處理。</p>



<pre class="prettyprint"><code class=" hljs javascript"><span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">y</span><span class="hljs-params">(b)</span> {</span>
    <span class="hljs-keyword">var</span> a = <span class="hljs-number">12</span>;
    <span class="hljs-keyword">return</span> a+b+<span class="hljs-number">35</span>;
}

<span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">x</span><span class="hljs-params">(p)</span> {</span>
    <span class="hljs-keyword">var</span> m = <span class="hljs-number">4</span>;
    <span class="hljs-keyword">return</span> y(m*p);
}

x(<span class="hljs-number">21</span>);</code></pre>

<p>當函式 <em>x</em> 被執行時，第一個框架「frame」會被產生，框架內會包含 <em>x</em> 裡面使用到的參數與區域變數。當 <em>x</em> 呼叫 <em>y</em> 時，第二個框架也被產生，同時被疊在<strong>框架一</strong>的上面。當 <em>y</em> 執行完畢後，<strong>框架二</strong>會從堆疊裡面移除，這時後只剩下<strong>框架一</strong>在堆疊裡。當 <em>x</em> 執行完畢後<strong>框架一</strong>會從堆疊裡面移除，此時堆疊為空的。</p>

<p><strong>Heap 堆積</strong> <br>
物件在被產生時，都會在 Heap 裡產生一個記憶體區塊，但是以無順序的方式擺放。</p>

<p><strong>Queue 佇列</strong> <br>
Javascript 在執行時期都會產生一個佇列，佇列裡含有了一系列需要被處理的訊息，而每一則訊息都有與其相關的函式。處理訊息的流程如下；</p>



<div class="sequence-diagram"><svg style="overflow: hidden; position: relative; left: -0.349976px; top: -0.216797px;" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns="http://www.w3.org/2000/svg" width="805.5999946594238" version="1.1" height="501.6000061035156"><desc>Created with Raphaël 2.1.2</desc><defs><path id="raphael-marker-block" d="M5,0 0,2.5 5,5z" stroke-linecap="round"></path><marker refY="2.5" refX="2.5" orient="auto" markerWidth="5" markerHeight="5" id="raphael-marker-endblock55-obj32"><use stroke="none" fill="#000" stroke-width="1.0000" transform="rotate(180 2.5 2.5) scale(1,1)" xlink:href="#raphael-marker-block"></use></marker><marker refY="2.5" refX="2.5" orient="auto" markerWidth="5" markerHeight="5" id="raphael-marker-endblock55-obj38"><use stroke="none" fill="#000" stroke-width="1.0000" transform="rotate(180 2.5 2.5) scale(1,1)" xlink:href="#raphael-marker-block"></use></marker><marker refY="2.5" refX="2.5" orient="auto" markerWidth="5" markerHeight="5" id="raphael-marker-endblock55-obj44"><use stroke="none" fill="#000" stroke-width="1.0000" transform="rotate(180 2.5 2.5) scale(1,1)" xlink:href="#raphael-marker-block"></use></marker><marker refY="2.5" refX="2.5" orient="auto" markerWidth="5" markerHeight="5" id="raphael-marker-endblock55-obj47"><use stroke="none" fill="#000" stroke-width="1.0000" transform="rotate(180 2.5 2.5) scale(1,1)" xlink:href="#raphael-marker-block"></use></marker></defs><rect stroke-width="2" style="" stroke="#000000" fill="none" ry="0" rx="0" height="39.20000076293945" width="78.4000015258789" y="20" x="10"></rect><rect style="" stroke="none" fill="#ffffff" ry="0" rx="0" height="19.200000762939453" width="58.400001525878906" y="30" x="21.200000762939453"></rect><text fill="#000000" stroke="none" font-size="16px" font-family="Andale Mono, monospace" text-anchor="middle" y="39.60000038146973" x="49.20000076293945" style="text-anchor: middle; font-family: Andale Mono,monospace; font-size: 16px;"><tspan dy="5.600002288818359">Message</tspan></text><rect stroke-width="2" style="" stroke="#000000" fill="none" ry="0" rx="0" height="39.20000076293945" width="78.4000015258789" y="442.4000053405762" x="10"></rect><rect style="" stroke="none" fill="#ffffff" ry="0" rx="0" height="19.200000762939453" width="58.400001525878906" y="452.4000244140625" x="21.200000762939453"></rect><text fill="#000000" stroke="none" font-size="16px" font-family="Andale Mono, monospace" text-anchor="middle" y="462.0000057220459" x="49.20000076293945" style="text-anchor: middle; font-family: Andale Mono,monospace; font-size: 16px;"><tspan dy="5.600017547607422">Message</tspan></text><path stroke-width="2" d="M49.20000076293945,59.20000076293945L49.20000076293945,442.4000053405762" stroke="#000000" fill="none" style=""></path><rect stroke-width="2" style="" stroke="#000000" fill="none" ry="0" rx="0" height="39.20000076293945" width="40.79999923706055" y="20" x="225.600004196167"></rect><rect style="" stroke="none" fill="#ffffff" ry="0" rx="0" height="19.200000762939453" width="20.799999237060547" y="30" x="235.60000610351562"></rect><text fill="#000000" stroke="none" font-size="16px" font-family="Andale Mono, monospace" text-anchor="middle" y="39.60000038146973" x="246.00000381469727" style="text-anchor: middle; font-family: Andale Mono,monospace; font-size: 16px;"><tspan dy="5.600002288818359">X()</tspan></text><rect stroke-width="2" style="" stroke="#000000" fill="none" ry="0" rx="0" height="39.20000076293945" width="40.79999923706055" y="442.4000053405762" x="225.600004196167"></rect><rect style="" stroke="none" fill="#ffffff" ry="0" rx="0" height="19.200000762939453" width="20.799999237060547" y="452.4000244140625" x="235.60000610351562"></rect><text fill="#000000" stroke="none" font-size="16px" font-family="Andale Mono, monospace" text-anchor="middle" y="462.0000057220459" x="246.00000381469727" style="text-anchor: middle; font-family: Andale Mono,monospace; font-size: 16px;"><tspan dy="5.600017547607422">X()</tspan></text><path stroke-width="2" d="M246.00000381469727,59.20000076293945L246.00000381469727,442.4000053405762" stroke="#000000" fill="none" style=""></path><rect stroke-width="2" style="" stroke="#000000" fill="none" ry="0" rx="0" height="39.20000076293945" width="40" y="20" x="478.39999771118164"></rect><rect style="" stroke="none" fill="#ffffff" ry="0" rx="0" height="19.200000762939453" width="20" y="30" x="488.3999938964844"></rect><text fill="#000000" stroke="none" font-size="16px" font-family="Andale Mono, monospace" text-anchor="middle" y="39.60000038146973" x="498.39999771118164" style="text-anchor: middle; font-family: Andale Mono,monospace; font-size: 16px;"><tspan dy="5.600002288818359">Y()</tspan></text><rect stroke-width="2" style="" stroke="#000000" fill="none" ry="0" rx="0" height="39.20000076293945" width="40" y="442.4000053405762" x="478.39999771118164"></rect><rect style="" stroke="none" fill="#ffffff" ry="0" rx="0" height="19.200000762939453" width="20" y="452.4000244140625" x="488.3999938964844"></rect><text fill="#000000" stroke="none" font-size="16px" font-family="Andale Mono, monospace" text-anchor="middle" y="462.0000057220459" x="498.39999771118164" style="text-anchor: middle; font-family: Andale Mono,monospace; font-size: 16px;"><tspan dy="5.600017547607422">Y()</tspan></text><path stroke-width="2" d="M498.39999771118164,59.20000076293945L498.39999771118164,442.4000053405762" stroke="#000000" fill="none" style=""></path><rect style="" stroke="none" fill="#ffffff" ry="0" rx="0" height="19.200000762939453" width="32.79999923706055" y="74.5999984741211" x="132"></rect><text fill="#000000" stroke="none" font-size="16px" font-family="Andale Mono, monospace" text-anchor="middle" y="84.20000076293945" x="147.60000228881836" style="text-anchor: middle; font-family: Andale Mono,monospace; font-size: 16px;"><tspan dy="5.600000381469727">calls</tspan></text><path stroke-dasharray="0" marker-end="url(#raphael-marker-endblock55-obj32)" stroke-width="2" d="M49.20000076293945,98.4000015258789C49.20000076293945,98.4000015258789,210.351078315108,98.4000015258789,240.99968412886273,98.4000015258789" stroke="#000000" fill="none" style=""></path><rect stroke-width="2" style="" stroke="#000000" fill="none" ry="0" rx="0" height="65.20000076293945" width="212.39999389648438" y="118.4000015258789" x="266.00000381469727"></rect><rect style="" stroke="none" fill="#ffffff" ry="0" rx="0" height="55.199989318847656" width="202.39999389648438" y="123.4000015258789" x="271.4000244140625"></rect><text fill="#000000" stroke="none" font-size="16px" font-family="Andale Mono, monospace" text-anchor="middle" y="151.00000190734863" x="372.20000076293945" style="text-anchor: middle; font-family: Andale Mono,monospace; font-size: 16px;"><tspan dy="-12.399999618530273">1. create 1st stack frame for X() </tspan><tspan x="372.20000076293945" dy="18"> 2. create heap for argument p </tspan><tspan x="372.20000076293945" dy="18"> 3. create heap for variable m</tspan></text><rect style="" stroke="none" fill="#ffffff" ry="0" rx="0" height="19.200000762939453" width="32.79999923706055" y="199" x="356.6000061035156"></rect><text fill="#000000" stroke="none" font-size="16px" font-family="Andale Mono, monospace" text-anchor="middle" y="208.60000228881836" x="372.20000076293945" style="text-anchor: middle; font-family: Andale Mono,monospace; font-size: 16px;"><tspan dy="5.599992752075195">calls</tspan></text><path stroke-dasharray="0" marker-end="url(#raphael-marker-endblock55-obj38)" stroke-width="2" d="M246.00000381469727,222.8000030517578C246.00000381469727,222.8000030517578,457.95432960444805,222.8000030517578,493.4007927797359,222.8000030517578" stroke="#000000" fill="none" style=""></path><rect stroke-width="2" style="" stroke="#000000" fill="none" ry="0" rx="0" height="65.20000076293945" width="217.1999969482422" y="242.8000030517578" x="518.3999977111816"></rect><rect style="" stroke="none" fill="#ffffff" ry="0" rx="0" height="55.20002746582031" width="207.20001220703125" y="247.8000030517578" x="523.7999877929688"></rect><text fill="#000000" stroke="none" font-size="16px" font-family="Andale Mono, monospace" text-anchor="middle" y="275.40000343322754" x="626.9999961853027" style="text-anchor: middle; font-family: Andale Mono,monospace; font-size: 16px;"><tspan dy="-12.399984359741211">1. create 2nd stack frame for Y() </tspan><tspan x="626.9999961853027" dy="18"> 2. create heap for argument b </tspan><tspan x="626.9999961853027" dy="18"> 3. create heap for variable a</tspan></text><rect style="" stroke="none" fill="#ffffff" ry="0" rx="0" height="37.20001220703125" width="182.39999389648438" y="314.4000244140625" x="282.20001220703125"></rect><text fill="#000000" stroke="none" font-size="16px" font-family="Andale Mono, monospace" text-anchor="middle" y="333.00000381469727" x="372.20000076293945" style="text-anchor: middle; font-family: Andale Mono,monospace; font-size: 16px;"><tspan dy="-3.3999900817871094">returns result and </tspan><tspan x="372.20000076293945" dy="18"> pop out the 2nd stack frame</tspan></text><path stroke-dasharray="6,2" marker-end="url(#raphael-marker-endblock55-obj44)" stroke-width="2" d="M498.39999771118164,365.2000045776367C498.39999771118164,365.2000045776367,286.44567192143086,365.2000045776367,250.99920874614295,365.2000045776367" stroke="#000000" fill="none" style=""></path><rect style="" stroke="none" fill="#ffffff" ry="0" rx="0" height="37.20001220703125" width="176.8000030517578" y="371.6000061035156" x="60.40000534057617"></rect><text fill="#000000" stroke="none" font-size="16px" font-family="Andale Mono, monospace" text-anchor="middle" y="390.2000045776367" x="147.60000228881836" style="text-anchor: middle; font-family: Andale Mono,monospace; font-size: 16px;"><tspan dy="-3.4000015258789062">returns result and </tspan><tspan x="147.60000228881836" dy="18"> pop out the 1st stack frame</tspan></text><path stroke-dasharray="6,2" marker-end="url(#raphael-marker-endblock55-obj47)" stroke-width="2" d="M246.00000381469727,422.4000053405762C246.00000381469727,422.4000053405762,84.84892626252872,422.4000053405762,54.20032044877401,422.4000053405762" stroke="#000000" fill="none" style=""></path></svg></div>

<div class="footnotes"><hr><ol><li id="fn:eventloop">參考資料來源為 <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/EventLoop">MDN</a>. <a href="#fnref:eventloop" title="Return to article" class="reversefootnote">↩</a></li></ol></div>