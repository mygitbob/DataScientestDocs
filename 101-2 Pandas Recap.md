---


---

<h2 id="introduction-to-dataframes">Introduction to DataFrames</h2>
<p>In this brief introduction, you have learned to:</p>
<ul>
<li>
<p>Create a  <code>DataFrame</code>  from a  <code>numpy</code>  array and a dictionary using the  <strong><code>pd.DataFrame</code></strong>  constructor.</p>
</li>
<li>
<p>Create a  <code>DataFrame</code>  from a  <code>.csv</code>  file using the  <strong><code>pd.read_csv</code></strong>  function.</p>
</li>
<li>
<p>Display the first and last lines of a  <code>DataFrame</code>  using the  <strong><code>head</code></strong>  and  <code>tail</code>  methods.</p>
</li>
<li>
<p>Select one or more columns of a  <code>DataFrame</code>  by entering their names in square brackets as in a dictionary.</p>
</li>
<li>
<p>Select one or more lines of a  <code>DataFrame</code>  by filling in their index using the  <strong><code>loc</code></strong>  and  <strong><code>iloc</code></strong>  methods.</p>
</li>
<li>
<p>Select the lines of a  <code>DataFrame</code>  that meet a specific condition using  <strong>conditional indexing</strong>.</p>
</li>
<li>
<p>Perform a quick statistical study of the quantitative variables of a  <code>DataFrame</code>  using the  <strong><code>describe</code></strong>  method.</p>
</li>
</ul>
<h2 id="data-cleaning-and-missing-values-management">Data Cleaning and Missing Values Management</h2>
<p>In this chapter we have seen the essential methods of the  <code>pandas</code>  module in order to clean up a dataset and manage missing values ​​(<code>NaN</code>).</p>
<p>This step of preparing a dataset is  <strong>always</strong>  the first step of a data project.</p>
<p>Regarding  <strong>data cleaning</strong>, we have learned how to:</p>
<ul>
<li>
<p>Identify and delete duplicates of a  <code>DataFrame</code>  using the  <strong><code>duplicated</code></strong>  and  <strong><code>drop_duplicates</code></strong>  methods.</p>
</li>
<li>
<p>Modify the elements of a  <code>DataFrame</code>  and their type using the  <strong><code>replace</code></strong>,  <strong><code>rename</code></strong>  and  <strong><code>astype</code></strong>  methods.</p>
</li>
<li>
<p>Apply a function to a  <code>DataFrame</code>  with the  <strong><code>apply</code></strong>  method and the  <strong><code>lambda</code></strong>  clause.</p>
</li>
</ul>
<p>Regarding the  <strong>management of missing values</strong>, we have learned to:</p>
<ul>
<li>
<p><strong>Detect</strong>  them using the  <strong><code>isna</code></strong>  method followed by the  <strong><code>any</code></strong>  and  <strong><code>sum</code></strong>  methods.</p>
</li>
<li>
<p><strong>Replace</strong>  them using the  <strong><code>fillna</code></strong>  method and the  <strong>statistical methods</strong>.</p>
</li>
<li>
<p><strong>Delete</strong>  them using the  <strong><code>dropna</code></strong>  method.</p>
</li>
</ul>
<h2 id="data-processing">Data processing</h2>
<ul>
<li><strong>Filter</strong>  the rows of a  <code>DataFrame</code>  with  <strong>multiple conditions</strong>  using the binary operators  <strong><code>&amp;</code></strong>,  <strong><code>|</code></strong>  and  <strong><code>-</code></strong>:</li>
</ul>
<pre class=" language-python"><code class="prism  language-python"><span class="token comment"># Year equal to 1979 and surface area greater than 60</span>
df<span class="token punctuation">[</span><span class="token punctuation">(</span>df<span class="token punctuation">[</span><span class="token string">'year'</span><span class="token punctuation">]</span> <span class="token operator">==</span> <span class="token number">1979</span><span class="token punctuation">)</span> <span class="token operator">&amp;</span> <span class="token punctuation">(</span>df<span class="token punctuation">[</span><span class="token string">'surface'</span><span class="token punctuation">]</span> <span class="token operator">&gt;</span> <span class="token number">60</span><span class="token punctuation">)</span><span class="token punctuation">]</span>

Year greater than <span class="token number">1900</span> <span class="token operator">or</span> neighborhood equal to <span class="token string">'Père-Lachaise'</span><span class="token punctuation">.</span>
df<span class="token punctuation">[</span><span class="token punctuation">(</span>df<span class="token punctuation">[</span><span class="token string">'year'</span><span class="token punctuation">]</span> <span class="token operator">&gt;</span> <span class="token number">1900</span><span class="token punctuation">)</span> <span class="token operator">|</span> <span class="token punctuation">(</span>df<span class="token punctuation">[</span><span class="token string">'neighborhood'</span><span class="token punctuation">]</span> <span class="token operator">==</span> <span class="token string">'Père-Lachaise'</span><span class="token punctuation">)</span><span class="token punctuation">]</span>
</code></pre>
<ul>
<li><strong>Merge</strong>  <code>DataFrames</code>  using the  <strong><code>concat</code></strong>  function and the  <strong><code>merge</code></strong>  method.</li>
</ul>
<pre class=" language-python"><code class="prism  language-python"><span class="token comment"># Vertical concatenation</span>
pd<span class="token punctuation">.</span>concat<span class="token punctuation">(</span><span class="token punctuation">[</span>df1<span class="token punctuation">,</span> df2<span class="token punctuation">]</span><span class="token punctuation">,</span> axis <span class="token operator">=</span> <span class="token number">0</span><span class="token punctuation">)</span>

<span class="token comment"># Horizontal concatenation</span>
pd<span class="token punctuation">.</span>concat<span class="token punctuation">(</span><span class="token punctuation">[</span>df1<span class="token punctuation">,</span> df2<span class="token punctuation">]</span><span class="token punctuation">,</span> axis <span class="token operator">=</span> <span class="token number">1</span><span class="token punctuation">)</span>

<span class="token comment"># Different types of joins</span>
df1<span class="token punctuation">.</span>merge<span class="token punctuation">(</span>right <span class="token operator">=</span> df2<span class="token punctuation">,</span> on <span class="token operator">=</span> <span class="token string">'column'</span><span class="token punctuation">,</span> how <span class="token operator">=</span> <span class="token string">'inner'</span><span class="token punctuation">)</span>
df1<span class="token punctuation">.</span>merge<span class="token punctuation">(</span>right <span class="token operator">=</span> df2<span class="token punctuation">,</span> on <span class="token operator">=</span> <span class="token string">'column'</span><span class="token punctuation">,</span> how <span class="token operator">=</span> <span class="token string">'outer'</span><span class="token punctuation">)</span>
df1<span class="token punctuation">.</span>merge<span class="token punctuation">(</span>right <span class="token operator">=</span> df2<span class="token punctuation">,</span> on <span class="token operator">=</span> <span class="token string">'column'</span><span class="token punctuation">,</span> how <span class="token operator">=</span> <span class="token string">'left'</span><span class="token punctuation">)</span>
df1<span class="token punctuation">.</span>merge<span class="token punctuation">(</span>right <span class="token operator">=</span> df2<span class="token punctuation">,</span> on <span class="token operator">=</span> <span class="token string">'column'</span><span class="token punctuation">,</span> how <span class="token operator">=</span> <span class="token string">'right'</span><span class="token punctuation">)</span>
</code></pre>
<ul>
<li><strong>Sort</strong>  and  <strong>order</strong>  the values of a  <code>DataFrame</code>  with the  <strong><code>sort_values</code></strong>  and  <strong><code>sort_index</code></strong>  methods.</li>
</ul>
<pre class=" language-python"><code class="prism  language-python"><span class="token comment"># Sorting a DataFrame by 'column' in ascending order</span>
df<span class="token punctuation">.</span>sort_values<span class="token punctuation">(</span>by <span class="token operator">=</span> <span class="token string">'column'</span><span class="token punctuation">,</span> ascending <span class="token operator">=</span> <span class="token boolean">True</span><span class="token punctuation">)</span>
</code></pre>
<ul>
<li>Perform a complex  <strong><code>groupby</code>  operation</strong>  using  <code>lambda</code>  functions and the  <strong><code>groupby</code></strong>  and  <strong><code>agg</code></strong>  methods.</li>
</ul>
<pre class=" language-py"><code class="prism  language-py">functions_to_apply <span class="token operator">=</span> <span class="token punctuation">{</span>
<span class="token string">'column1'</span><span class="token punctuation">:</span> <span class="token punctuation">[</span><span class="token string">'min'</span><span class="token punctuation">,</span> <span class="token string">'max'</span><span class="token punctuation">]</span><span class="token punctuation">,</span>
<span class="token string">'column2'</span> <span class="token punctuation">:</span> <span class="token punctuation">[</span>np<span class="token punctuation">.</span>mean<span class="token punctuation">,</span> np<span class="token punctuation">.</span>std<span class="token punctuation">]</span><span class="token punctuation">,</span>
<span class="token string">'column3'</span> <span class="token punctuation">:</span> <span class="token keyword">lambda</span> x<span class="token punctuation">:</span> x<span class="token punctuation">.</span><span class="token builtin">max</span><span class="token punctuation">(</span><span class="token punctuation">)</span> <span class="token operator">-</span> x<span class="token punctuation">.</span><span class="token builtin">min</span><span class="token punctuation">(</span><span class="token punctuation">)</span>
<span class="token punctuation">}</span>

df<span class="token punctuation">.</span>groupby<span class="token punctuation">(</span><span class="token string">'column_to_group_by'</span><span class="token punctuation">)</span><span class="token punctuation">.</span>agg<span class="token punctuation">(</span>functions_to_apply<span class="token punctuation">)</span>
</code></pre>

