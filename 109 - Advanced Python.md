---


---

<h2 id="annotations">Annotations</h2>
<p><strong>BSP:</strong></p>
<pre class=" language-python"><code class="prism  language-python"><span class="token keyword">def</span> <span class="token function">a_function</span><span class="token punctuation">(</span>a <span class="token punctuation">:</span> <span class="token builtin">str</span><span class="token operator">=</span><span class="token string">'Hello World'</span><span class="token punctuation">)</span> <span class="token operator">-</span><span class="token operator">&gt;</span> <span class="token boolean">None</span> <span class="token punctuation">:</span> 
   <span class="token keyword">print</span><span class="token punctuation">(</span>a<span class="token punctuation">)</span>
</code></pre>
<p>Kann abgefragt werden mit</p>
<pre class=" language-python"><code class="prism  language-python"><span class="token keyword">print</span><span class="token punctuation">(</span>a_function<span class="token punctuation">.</span>__annotations__<span class="token punctuation">)</span>
</code></pre>
<h2 id="multithreating-and-multiprocessing">Multithreating and multiprocessing</h2>
<h4 id="threading">Threading</h4>
<pre class=" language-py"><code class="prism  language-py"><span class="token keyword">from</span> threading <span class="token keyword">import</span> Thread

<span class="token keyword">def</span> <span class="token function">dummy</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">:</span><span class="token keyword">pass</span>

th1 <span class="token operator">=</span> Thread<span class="token punctuation">(</span>taget<span class="token operator">=</span>dummy<span class="token punctuation">)</span>
th1<span class="token punctuation">.</span>start<span class="token punctuation">(</span><span class="token punctuation">)</span>
th1<span class="token punctuation">.</span>join<span class="token punctuation">(</span><span class="token punctuation">)</span>
</code></pre>
<h3 id="multiprocessing-v1">Multiprocessing V1</h3>
<pre class=" language-py"><code class="prism  language-py"><span class="token keyword">import</span> multiprocessing
<span class="token keyword">from</span> multiprocessing <span class="token keyword">import</span> Pool

<span class="token keyword">def</span> <span class="token function">dummy2</span><span class="token punctuation">(</span>x<span class="token punctuation">)</span><span class="token punctuation">:</span> <span class="token keyword">return</span> x<span class="token operator">**</span>x
pool <span class="token operator">=</span> Pool<span class="token punctuation">(</span><span class="token number">4</span><span class="token punctuation">)</span>  <span class="token comment"># Processes are created</span>

result <span class="token operator">=</span> pool<span class="token punctuation">.</span><span class="token builtin">map</span><span class="token punctuation">(</span>
	dummy2<span class="token punctuation">,</span>
    <span class="token punctuation">[</span><span class="token builtin">range</span><span class="token punctuation">(</span><span class="token number">1000000</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
     <span class="token builtin">range</span><span class="token punctuation">(</span><span class="token number">5000000</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
     <span class="token builtin">range</span><span class="token punctuation">(</span><span class="token number">4000000</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
     <span class="token builtin">range</span><span class="token punctuation">(</span><span class="token number">7000000</span><span class="token punctuation">)</span><span class="token punctuation">]</span><span class="token punctuation">)</span>
</code></pre>
<h3 id="multiprocessing-v2">Multiprocessing V2</h3>
<pre class=" language-py"><code class="prism  language-py"><span class="token keyword">from</span> multiprocessing <span class="token keyword">import</span> Process

number <span class="token operator">=</span> <span class="token punctuation">[</span><span class="token builtin">range</span><span class="token punctuation">(</span><span class="token number">10000</span><span class="token punctuation">)</span><span class="token punctuation">,</span> <span class="token builtin">range</span><span class="token punctuation">(</span><span class="token number">20000</span><span class="token punctuation">)</span><span class="token punctuation">,</span> <span class="token builtin">range</span><span class="token punctuation">(</span><span class="token number">30000</span><span class="token punctuation">)</span><span class="token punctuation">]</span>
<span class="token keyword">def</span> <span class="token function">dummy3</span><span class="token punctuation">(</span>x<span class="token punctuation">)</span><span class="token punctuation">:</span> <span class="token keyword">return</span> x<span class="token operator">**</span>x
processes <span class="token operator">=</span> <span class="token punctuation">[</span>Process<span class="token punctuation">(</span>target<span class="token operator">=</span>dummy3<span class="token punctuation">,</span> args<span class="token operator">=</span><span class="token punctuation">(</span>num<span class="token punctuation">,</span><span class="token punctuation">)</span><span class="token punctuation">)</span> <span class="token keyword">for</span> num <span class="token keyword">in</span> numbers<span class="token punctuation">]</span>
<span class="token keyword">for</span> p <span class="token keyword">in</span> processes<span class="token punctuation">:</span>
	p<span class="token punctuation">.</span>start<span class="token punctuation">(</span><span class="token punctuation">)</span>
<span class="token keyword">for</span> p <span class="token keyword">in</span> processes<span class="token punctuation">:</span>
	p<span class="token punctuation">.</span>join<span class="token punctuation">(</span><span class="token punctuation">)</span>
</code></pre>
<h2 id="asynchronous-functions">Asynchronous Functions</h2>
<h3 id="standalone-version">Standalone Version</h3>
<pre class=" language-py"><code class="prism  language-py"><span class="token keyword">import</span> asyncio

<span class="token keyword">async</span> <span class="token keyword">def</span> <span class="token function">function1</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">:</span>
    <span class="token keyword">print</span><span class="token punctuation">(</span><span class="token string">"Function 1 start"</span><span class="token punctuation">)</span>
    <span class="token keyword">await</span> asyncio<span class="token punctuation">.</span>sleep<span class="token punctuation">(</span><span class="token number">3</span><span class="token punctuation">)</span>
    <span class="token keyword">print</span><span class="token punctuation">(</span><span class="token string">"Function 1 done"</span><span class="token punctuation">)</span>

<span class="token keyword">async</span> <span class="token keyword">def</span> <span class="token function">function2</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">:</span>
    <span class="token keyword">print</span><span class="token punctuation">(</span><span class="token string">"Function 2 done"</span><span class="token punctuation">)</span>
    <span class="token keyword">await</span> asyncio<span class="token punctuation">.</span>sleep<span class="token punctuation">(</span><span class="token number">2</span><span class="token punctuation">)</span>
    <span class="token keyword">print</span><span class="token punctuation">(</span><span class="token string">"Function 2 done"</span><span class="token punctuation">)</span>

<span class="token keyword">async</span> <span class="token keyword">def</span> <span class="token function">main</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">:</span>
    <span class="token keyword">await</span> asyncio<span class="token punctuation">.</span>gather<span class="token punctuation">(</span>function1<span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">,</span> function2<span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">)</span>

<span class="token comment"># Run the main coroutine</span>
asyncio<span class="token punctuation">.</span>run<span class="token punctuation">(</span>main<span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">)</span>
</code></pre>
<h3 id="jupyter-notebook-version">Jupyter Notebook Version</h3>
<p><strong>Unterschied nur in letzter Zeile</strong></p>
<pre class=" language-py"><code class="prism  language-py"><span class="token keyword">await</span> main<span class="token punctuation">(</span><span class="token punctuation">)</span>
</code></pre>
<h3 id="ensure-future">Ensure future</h3>
<pre class=" language-py"><code class="prism  language-py"><span class="token keyword">async</span> <span class="token keyword">def</span> <span class="token function">function1</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">:</span>
    <span class="token keyword">await</span> asyncio<span class="token punctuation">.</span>sleep<span class="token punctuation">(</span><span class="token number">3</span><span class="token punctuation">)</span>
    <span class="token keyword">print</span><span class="token punctuation">(</span><span class="token string">"Function 1 done"</span><span class="token punctuation">)</span>

<span class="token keyword">async</span> <span class="token keyword">def</span> <span class="token function">function2</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">:</span>
    <span class="token keyword">await</span> asyncio<span class="token punctuation">.</span>sleep<span class="token punctuation">(</span><span class="token number">2</span><span class="token punctuation">)</span>
    <span class="token keyword">print</span><span class="token punctuation">(</span><span class="token string">"Function 2 done"</span><span class="token punctuation">)</span>

<span class="token keyword">async</span> <span class="token keyword">def</span> <span class="token function">main</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">:</span>
    task1 <span class="token operator">=</span> asyncio<span class="token punctuation">.</span>ensure_future<span class="token punctuation">(</span>function1<span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">)</span>
    task2 <span class="token operator">=</span> asyncio<span class="token punctuation">.</span>ensure_future<span class="token punctuation">(</span>function2<span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">)</span>
    <span class="token keyword">await</span> task1
    <span class="token keyword">await</span> task2

asyncio<span class="token punctuation">.</span>run<span class="token punctuation">(</span>main<span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">)</span> <span class="token comment"># bzw. await main() in Jupyter Notebook</span>

</code></pre>
<h3 id="unterschied-asyncio.gather-und-asyncio.ensure_future">Unterschied asyncio.gather und asyncio.ensure_future</h3>
<p><code>asyncio.gather</code> und <code>asyncio.ensure_future</code> (nicht <code>asyncio.enable_future</code>) sind zwei Funktionen in der <code>asyncio</code>-Bibliothek, die für verschiedene Zwecke verwendet werden.</p>
<ol>
<li>
<p><strong><code>asyncio.gather</code></strong>:</p>
<ul>
<li>Die <code>asyncio.gather</code>-Funktion wird verwendet, um mehrere asynchrone Aufgaben gleichzeitig auszuführen und die Ergebnisse zu sammeln.</li>
<li>Es akzeptiert eine beliebige Anzahl von awaitable Objekten (wie Coroutinen oder Futures) und führt sie gleichzeitig aus.</li>
<li><code>gather</code> gibt eine zukünftige Ergebnisliste zurück, die die Ergebnisse der übergebenen awaitable Objekte enthält, wenn sie abgeschlossen sind.</li>
</ul>
<p>Beispiel:<br>
<code>await asyncio.gather(task1(), task2(), task3())</code></p>
</li>
<li>
<p><strong><code>asyncio.ensure_future</code></strong>:</p>
<ul>
<li>Die <code>asyncio.ensure_future</code>-Funktion wird verwendet, um eine einzelne asynchrone Aufgabe zu planen, ohne sie sofort auszuführen.</li>
<li>Es akzeptiert eine awaitable Aufgabe und gibt eine zukünftige Instanz zurück, die diese Aufgabe repräsentiert.</li>
<li>Die Aufgabe wird sofort zur Ausführung geplant und kann später überwacht werden.</li>
</ul>
<p>Beispiel:<br>
<code>future = asyncio.ensure_future(task())</code></p>
</li>
</ol>
<p>Der Hauptunterschied besteht also darin, dass <code>asyncio.gather</code> verwendet wird, um mehrere asynchrone Aufgaben gleichzeitig auszuführen und ihre Ergebnisse zu sammeln, während <code>asyncio.ensure_future</code> verwendet wird, um eine einzelne asynchrone Aufgabe zu planen und auszuführen.</p>

