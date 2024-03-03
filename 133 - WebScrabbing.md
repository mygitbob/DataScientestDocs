---


---

<h2 id="allgemein">Allgemein</h2>
<h3 id="css">CSS</h3>
<p>Klassen beginnen mit <code>.</code>, zB <code>.my_class</code><br>
ID beginnen mit <code>#</code>, zB <code>#my_id</code></p>
<h3 id="http-response-codes">HTTP Response Codes</h3>
<ul>
<li><strong>1XX</strong>  : Information</li>
<li><strong>2XX</strong>  : Success</li>
<li><strong>3XX</strong>  : Redirection</li>
<li><strong>4XX</strong>  : Client error</li>
<li><strong>5XX</strong>  : Server error</li>
</ul>
<h3 id="python-requests-library">Python Requests Library</h3>
<pre class=" language-py"><code class="prism  language-py"><span class="token keyword">import</span> requests

res <span class="token operator">=</span> requests<span class="token punctuation">.</span>get<span class="token punctuation">(</span><span class="token string">'https://www.welcometothejungle.com/en'</span><span class="token punctuation">)</span>

<span class="token keyword">print</span><span class="token punctuation">(</span>res<span class="token punctuation">)</span>			<span class="token comment"># -&gt; Response Code</span>
<span class="token keyword">print</span><span class="token punctuation">(</span>res<span class="token punctuation">.</span>content<span class="token punctuation">)</span>	<span class="token comment"># -&gt; Html Source</span>
</code></pre>
<h2 id="beautifulsoup">BeautifulSoup</h2>
<h3 id="parser">Parser</h3>
<ul>
<li>html.parser<br>
default, vorinstalliert</li>
<li>html5lib<br>
Ressourcenhungrig und langsam, aber kann html5  features</li>
<li>lxml<br>
kann auch xml parsen, wird bevorzugt</li>
</ul>
<h3 id="bs-beispiel">BS Beispiel</h3>
<pre class=" language-py"><code class="prism  language-py"><span class="token keyword">from</span> bs4 <span class="token keyword">import</span> BeautifulSoup <span class="token keyword">as</span> bs
<span class="token keyword">import</span> requests 

url <span class="token operator">=</span> <span class="token string">'https://en.wikipedia.org/wiki/Alan_Turing'</span>
page <span class="token operator">=</span> requests<span class="token punctuation">.</span>get<span class="token punctuation">(</span>url<span class="token punctuation">)</span>
soup <span class="token operator">=</span> bs<span class="token punctuation">(</span>page<span class="token punctuation">.</span>content<span class="token punctuation">,</span> <span class="token string">"lxml"</span><span class="token punctuation">)</span>
<span class="token keyword">print</span><span class="token punctuation">(</span>soup<span class="token punctuation">)</span>
</code></pre>
<h3 id="find">find()</h3>
<pre class=" language-py"><code class="prism  language-py">element <span class="token operator">=</span> bs<span class="token punctuation">.</span>find<span class="token punctuation">(</span><span class="token string">'Name des Tags'</span><span class="token punctuation">,</span> 
			class_ <span class="token operator">=</span> <span class="token string">'Klasse die gesucht wird'</span><span class="token punctuation">,</span> 
			<span class="token builtin">id</span> <span class="token operator">=</span> <span class="token string">'id die gesucht wird'</span><span class="token punctuation">,</span> <span class="token punctuation">.</span><span class="token punctuation">.</span><span class="token punctuation">.</span><span class="token punctuation">)</span>
</code></pre>
<p>*<strong>Achtung, <code>class_</code>verwenden wegen reserviertem key word</strong><br>
Man kann entweder:</p>
<pre class=" language-py"><code class="prism  language-py">bs<span class="token punctuation">.</span>find<span class="token punctuation">(</span><span class="token string">'div'</span><span class="token punctuation">)</span><span class="token punctuation">.</span>find<span class="token punctuation">(</span><span class="token string">'div'</span><span class="token punctuation">)</span><span class="token punctuation">.</span>find<span class="token punctuation">(</span><span class="token string">'a'</span><span class="token punctuation">)</span>
</code></pre>
<p>oder</p>
<pre class=" language-py"><code class="prism  language-py">bs<span class="token punctuation">.</span>div<span class="token punctuation">.</span>div<span class="token punctuation">.</span>a
</code></pre>
<p>benutzen</p>
<h3 id="find_all">find_all()</h3>
<pre class=" language-py"><code class="prism  language-py">all_div_content <span class="token operator">=</span> soup<span class="token punctuation">.</span>find_all<span class="token punctuation">(</span><span class="token string">'div'</span><span class="token punctuation">,</span> class_<span class="token operator">=</span><span class="token string">'content'</span><span class="token punctuation">)</span>
<span class="token keyword">for</span> val <span class="token keyword">in</span> all_div_content<span class="token punctuation">:</span>
    <span class="token keyword">print</span><span class="token punctuation">(</span>val<span class="token punctuation">.</span>text<span class="token punctuation">)</span>
</code></pre>
<h3 id="find_next-find_next_sibling">find_next(), find_next_sibling()</h3>
<p>In BeautifulSoup, <code>find_next()</code> und <code>find_next_sibling()</code> sind zwei verschiedene Methoden, die dazu dienen, im HTML-Dokument nach bestimmten Elementen zu suchen. Hier sind die Unterschiede:</p>
<ol>
<li>
<p><strong><code>find_next()</code></strong>:</p>
<ul>
<li>Die <code>find_next()</code>-Methode sucht nach dem nächsten Vorkommen eines bestimmten HTML-Elements, das den angegebenen Selektorbedingungen entspricht, unabhängig davon, ob es ein Geschwister-Element ist oder nicht.</li>
<li>Es berücksichtigt Elemente, die sowohl vor als auch nach dem aktuellen Element im HTML-Dokument stehen können.</li>
</ul>
<p>Beispiel:<br>
<code>current_element.find_next('p')</code></p>
</li>
<li>
<p><strong><code>find_next_sibling()</code></strong>:</p>
<ul>
<li>Die <code>find_next_sibling()</code>-Methode sucht speziell nach dem nächsten Geschwister-Element des aktuellen Elements.</li>
<li>Es ignoriert Elemente, die vor dem aktuellen Element stehen, und sucht nur nach dem nächsten Geschwister-Element auf der gleichen Hierarchieebene.</li>
</ul>
<p>Beispiel:<br>
<code>current_element.find_next_sibling('p')</code></p>
</li>
</ol>
<p>In beiden Fällen kannst du einen HTML-Selektor oder eine Funktion als Argument übergeben, um das gewünschte Element genauer zu spezifizieren. Diese Methoden sind besonders nützlich, wenn du durch das HTML navigierst und nach bestimmten Elementen suchst, die in einer bestimmten Reihenfolge oder Hierarchie auftreten.</p>
<h3 id="select">select()</h3>
<p>The  <code>select()</code>  function allows you to search for  <code>HTML</code>  elements using  <code>CSS</code>  selectors. This function offers a flexible approach to selecting  <code>HTML</code>  elements based on their position, their relationship to other elements or their attributes. In particular, the function allows :</p>
<ul>
<li>select elements based solely on their css attributes (class, id) using the <code>.</code> and <code>#</code> css selectors.</li>
<li>select elements from tags in a similar way to the  <code>find()</code>  function.</li>
<li>select elements by parent-child relationship: to do this, use the <code>&gt;</code> operator between  <code>CSS</code>  selectors.</li>
</ul>
<p>This function returns a list containing all the tags concerned by the query. If we want to directly access the first element in this list, i.e. the first <code>HTML</code> element that meets the criteria, we can use the <code>select_one()</code> function.</p>
<p><strong>BSP</strong></p>
<pre class=" language-py"><code class="prism  language-py">elements_css_class <span class="token operator">=</span> soup<span class="token punctuation">.</span>select<span class="token punctuation">(</span><span class="token string">'.chip'</span><span class="token punctuation">)</span>     <span class="token comment"># an HTML element whose class ('.' in css) is "chip".</span>
elements_css_id <span class="token operator">=</span> soup<span class="token punctuation">.</span>select<span class="token punctuation">(</span><span class="token string">'#second'</span><span class="token punctuation">)</span>      <span class="token comment"># an HTML element whose id ('#' in css) is "second".</span>
elements_parent_children <span class="token operator">=</span> soup<span class="token punctuation">.</span>select_one<span class="token punctuation">(</span><span class="token string">'div &gt; p'</span><span class="token punctuation">)</span> <span class="token comment"># the first paragraph inside a div</span>


<span class="token keyword">for</span> element <span class="token keyword">in</span> elements_css_class <span class="token punctuation">:</span> <span class="token comment"># browses the list of tags affected by the 'chip' class</span>
    <span class="token keyword">print</span><span class="token punctuation">(</span><span class="token string">" Element .chip class: "</span><span class="token punctuation">,</span> element<span class="token punctuation">.</span>text<span class="token punctuation">)</span>
    
<span class="token keyword">print</span><span class="token punctuation">(</span>elements_css_id<span class="token punctuation">[</span><span class="token number">0</span><span class="token punctuation">]</span><span class="token punctuation">.</span>text<span class="token punctuation">)</span>      <span class="token comment"># We access to the 1st element of the returned list</span>
<span class="token keyword">print</span><span class="token punctuation">(</span>elements_parent_children<span class="token punctuation">.</span>text<span class="token punctuation">)</span> 
</code></pre>
<h3 id="has_attr">has_attr()</h3>

