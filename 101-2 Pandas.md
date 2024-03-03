---


---

<h2 id="creation-of-a-dataframe">Creation of a DataFrame</h2>
<h4 id="from-a-numpy-array">from a numpy array</h4>
<p><strong><code>pd.DataFrame(data, index, columns, ...)</code></strong></p>
<p><strong>BSP:</strong></p>
<pre class=" language-py"><code class="prism  language-py"><span class="token comment"># Creation of a NumPy array with 3 rows and 4 columns</span>
array <span class="token operator">=</span> np<span class="token punctuation">.</span>array <span class="token punctuation">(</span><span class="token punctuation">[</span><span class="token punctuation">[</span><span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">2</span><span class="token punctuation">,</span> <span class="token number">3</span><span class="token punctuation">,</span> <span class="token number">4</span><span class="token punctuation">]</span><span class="token punctuation">,</span>
                   <span class="token punctuation">[</span><span class="token number">5</span><span class="token punctuation">,</span> <span class="token number">6</span><span class="token punctuation">,</span> <span class="token number">7</span><span class="token punctuation">,</span> <span class="token number">8</span><span class="token punctuation">]</span><span class="token punctuation">,</span>
                   <span class="token punctuation">[</span><span class="token number">9</span><span class="token punctuation">,</span> <span class="token number">10</span><span class="token punctuation">,</span> <span class="token number">11</span><span class="token punctuation">,</span> <span class="token number">12</span><span class="token punctuation">]</span><span class="token punctuation">]</span><span class="token punctuation">)</span>

<span class="token comment"># Instantiation of a DataFrame</span>
df <span class="token operator">=</span> pd<span class="token punctuation">.</span>DataFrame <span class="token punctuation">(</span>data <span class="token operator">=</span> array<span class="token punctuation">,</span> <span class="token comment"># The data to format</span>
                   index <span class="token operator">=</span> <span class="token punctuation">[</span><span class="token string">'i_1'</span><span class="token punctuation">,</span> <span class="token string">'i_2'</span><span class="token punctuation">,</span> <span class="token string">'i_3'</span><span class="token punctuation">]</span><span class="token punctuation">,</span> <span class="token comment"># The indices of each entry</span>
                   columns <span class="token operator">=</span> <span class="token punctuation">[</span><span class="token string">'A'</span><span class="token punctuation">,</span> <span class="token string">'B'</span><span class="token punctuation">,</span> <span class="token string">'C'</span><span class="token punctuation">,</span> <span class="token string">'D'</span><span class="token punctuation">]</span><span class="token punctuation">)</span> <span class="token comment"># The name of the columns</span>
</code></pre>
<h4 id="from-a-dictionary">from a dictionary</h4>
<p><strong>BSP:</strong></p>
<pre class=" language-py"><code class="prism  language-py"><span class="token comment"># Creation of a dictionary</span>
dictionary <span class="token operator">=</span> <span class="token punctuation">{</span><span class="token string">'A'</span><span class="token punctuation">:</span> <span class="token punctuation">[</span><span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">5</span><span class="token punctuation">,</span> <span class="token number">9</span><span class="token punctuation">]</span><span class="token punctuation">,</span>
              <span class="token string">'B'</span><span class="token punctuation">:</span> <span class="token punctuation">[</span><span class="token number">2</span><span class="token punctuation">,</span> <span class="token number">6</span><span class="token punctuation">,</span> <span class="token number">10</span><span class="token punctuation">]</span><span class="token punctuation">,</span>
              <span class="token string">'C'</span><span class="token punctuation">:</span> <span class="token punctuation">[</span><span class="token number">3</span><span class="token punctuation">,</span> <span class="token number">7</span><span class="token punctuation">,</span> <span class="token number">11</span><span class="token punctuation">]</span><span class="token punctuation">,</span>
              <span class="token string">'D'</span><span class="token punctuation">:</span> <span class="token punctuation">[</span><span class="token number">4</span><span class="token punctuation">,</span> <span class="token number">8</span><span class="token punctuation">,</span> <span class="token number">12</span><span class="token punctuation">]</span><span class="token punctuation">}</span>

<span class="token comment"># Instantiation of a DataFrame</span>
df <span class="token operator">=</span> pd<span class="token punctuation">.</span>DataFrame <span class="token punctuation">(</span>data <span class="token operator">=</span> dictionary<span class="token punctuation">,</span>
                   index <span class="token operator">=</span> <span class="token punctuation">[</span><span class="token string">'i_1'</span><span class="token punctuation">,</span> <span class="token string">'i_2'</span><span class="token punctuation">,</span> <span class="token string">'i_3'</span><span class="token punctuation">]</span><span class="token punctuation">)</span>
</code></pre>
<h4 id="from-a-file">from a file</h4>
<p><strong><code>pd.read_csv(filepath_or_buffer, sep = ',', header = 0, index_col = 0 ...)</code></strong></p>
<ul>
<li>
<p><strong><code>filepath_or_buffer</code></strong>: The  <strong>path</strong>  of the .csv file relative to the execution environment.</p>
<ul>
<li>If the file is in the same folder as the Python environment, just fill in the name of the file.</li>
<li>This path must be entered in the form of  <strong>character string</strong>.</li>
</ul>
</li>
<li>
<p><strong><code>sep</code></strong>: The character used in the .csv file to  <strong>separate</strong>  the different columns.</p>
<ul>
<li>This argument must be specified as  <strong>character</strong>.</li>
</ul>
</li>
<li>
<p><strong><code>header</code></strong>: The  <strong>number of the row</strong>  that contains the  <strong>names</strong>  of the columns.</p>
<ul>
<li>If for example the column names are entered in the  <strong>first</strong>  line of the  <code>.csv</code>  file, then we must specify  <strong><code>header = 0</code></strong>.</li>
<li>If the names are  <strong>not included</strong>, we will put  <strong><code>header = None</code></strong>.</li>
</ul>
</li>
<li>
<p><strong><code>index_col</code></strong>: The  <strong>name or number of the column</strong>  containing the  <strong>indices</strong>  of the database.</p>
<ul>
<li>If the database entries are indexed by the first column, you will need to fill in  <strong><code>index_col = 0</code></strong>.</li>
<li>Alternatively, if the entries are indexed by a column which bears the name  <code>"Id"</code>, we can specify  <strong><code>index_col = "Id"</code></strong>.</li>
</ul>
</li>
</ul>
<h2 id="visualization-of-a--dataframe">Visualization of a  <code>DataFrame</code></h2>
<h4 id="head">head()</h4>
<h4 id="tail">tail()</h4>
<h4 id="columns-attribute">columns (attribute)</h4>
<h4 id="shape-attribute">shape (attribute)</h4>
<h4 id="dtypes-attribute">dtypes (attribute)</h4>
<h4 id="describe-für-nummerische-werte">describe() (für nummerische Werte)</h4>
<h4 id="value_counts-für-kategorische-werte">value_counts() (für kategorische Werte)</h4>
<h2 id="slicing-in-einem-pandas-dataframe">Slicing in einem Pandas DataFrame</h2>
<ol>
<li><strong>Zeilen basierend auf Positionen selektieren</strong>:</li>
</ol>
<pre class=" language-py"><code class="prism  language-py"><span class="token comment"># Zeilen von Index 0 bis 4 (exklusiv) auswählen</span>
subset <span class="token operator">=</span> df<span class="token punctuation">.</span>iloc<span class="token punctuation">[</span><span class="token number">0</span><span class="token punctuation">:</span><span class="token number">4</span><span class="token punctuation">]</span>
</code></pre>
<ol start="2">
<li><strong>Bestimmte Zeilen basierend auf Bedingungen selektieren</strong>:</li>
</ol>
<pre class=" language-py"><code class="prism  language-py"><span class="token comment"># Zeilen auswählen, bei denen eine Bedingung erfüllt ist (z. B. Werte in einer Spalte)</span>
subset <span class="token operator">=</span> df<span class="token punctuation">[</span>df<span class="token punctuation">[</span><span class="token string">'Spalte'</span><span class="token punctuation">]</span> <span class="token operator">&gt;</span> Wert<span class="token punctuation">]</span>
</code></pre>
<ol start="3">
<li><strong>Bestimmte Spalten auswählen</strong>:</li>
</ol>
<pre class=" language-py"><code class="prism  language-py"><span class="token comment"># Eine oder mehrere Spalten auswählen</span>
subset <span class="token operator">=</span> df<span class="token punctuation">[</span><span class="token punctuation">[</span><span class="token string">'Spalte1'</span><span class="token punctuation">,</span> <span class="token string">'Spalte2'</span><span class="token punctuation">]</span><span class="token punctuation">]</span>
</code></pre>
<ol start="4">
<li><strong>Bestimmte Zeilen und Spalten auswählen</strong>:</li>
</ol>
<pre class=" language-py"><code class="prism  language-py"><span class="token comment"># Zeilen und Spalten basierend auf Positionen auswählen</span>
subset <span class="token operator">=</span> df<span class="token punctuation">.</span>iloc<span class="token punctuation">[</span><span class="token number">0</span><span class="token punctuation">:</span><span class="token number">3</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">:</span><span class="token number">4</span><span class="token punctuation">]</span>
<span class="token comment"># Oder Zeilen und Spalten basierend auf Labels auswählen</span>
subset <span class="token operator">=</span> df<span class="token punctuation">.</span>loc<span class="token punctuation">[</span><span class="token punctuation">[</span><span class="token string">'Index1'</span><span class="token punctuation">,</span> <span class="token string">'Index2'</span><span class="token punctuation">]</span><span class="token punctuation">,</span> <span class="token punctuation">[</span><span class="token string">'Spalte1'</span><span class="token punctuation">,</span> <span class="token string">'Spalte2'</span><span class="token punctuation">]</span><span class="token punctuation">]</span>
</code></pre>
<ol start="5">
<li><strong>Einzelne Elemente auswählen</strong>:</li>
</ol>
<pre class=" language-py"><code class="prism  language-py"><span class="token comment"># Einzelnes Element auswählen (Zeile, Spalte)</span>
value <span class="token operator">=</span> df<span class="token punctuation">.</span>at<span class="token punctuation">[</span><span class="token string">'Index'</span><span class="token punctuation">,</span> <span class="token string">'Spalte'</span><span class="token punctuation">]</span>
</code></pre>
<h2 id="data-cleaning-and-missing-values-management">Data Cleaning and Missing Values Management</h2>
<h3 id="managing-duplicates-duplicated--and--drop_duplicates--methods">Managing duplicates (<code>duplicated</code>  and  <code>drop_duplicates</code>  methods)</h3>
<pre class=" language-py"><code class="prism  language-py"><span class="token comment"># We identify the rows containing duplicates</span>
df<span class="token punctuation">.</span>duplicated<span class="token punctuation">(</span><span class="token punctuation">)</span>

<span class="token operator">&gt;&gt;</span><span class="token operator">&gt;</span> <span class="token number">0</span> <span class="token boolean">False</span>
<span class="token operator">&gt;&gt;</span><span class="token operator">&gt;</span> <span class="token number">1</span> <span class="token boolean">False</span>
<span class="token operator">&gt;&gt;</span><span class="token operator">&gt;</span> <span class="token number">2</span> <span class="token boolean">False</span>
<span class="token operator">&gt;&gt;</span><span class="token operator">&gt;</span> <span class="token number">3</span> <span class="token boolean">True</span>		<span class="token comment"># nur beim Duplikat True, </span>
				<span class="token comment"># Orginal bleibt False</span>
</code></pre>
<pre class=" language-py"><code class="prism  language-py">drop_duplicates<span class="token punctuation">(</span>subset<span class="token punctuation">,</span> keep<span class="token punctuation">,</span> inplace<span class="token punctuation">)</span>
</code></pre>
<ul>
<li>
<p>The  <code>subset</code>  parameter indicates the column(s) to consider in order to identify and remove duplicates. By default,  <strong><code>subset = None</code></strong>  namely we consider  <strong>all</strong>  the columns of the  <code>DataFrame</code>.</p>
<ul>
<li>The  <code>keep</code>  parameter indicates which entry should be kept :</li>
<li><strong><code>'first'</code></strong>  : We keep the  <strong>first</strong>  occurrence.</li>
<li><strong><code>'last'</code></strong>: We keep the  <strong>last</strong>  occurrence.</li>
<li><strong><code>False</code></strong>: We do not keep  <strong>any</strong>  occurrence.</li>
<li>By default,  <strong><code>keep = 'first'</code></strong>.</li>
</ul>
</li>
</ul>
<p><strong>BSP:</strong></p>
<pre class=" language-py"><code class="prism  language-py"><span class="token comment"># We keep only the first occurrence of the duplicate</span>
df_first <span class="token operator">=</span> df<span class="token punctuation">.</span>drop_duplicates<span class="token punctuation">(</span>keep <span class="token operator">=</span> <span class="token string">'first'</span><span class="token punctuation">)</span>
</code></pre>
<h3 id="modification-of-the-elements-of-a--dataframe--replace--rename--and--astype--methods">Modification of the elements of a  <code>DataFrame</code>  (<code>replace</code>,  <code>rename</code>  and  <code>astype</code>  methods)</h3>
<h4 id="replaceto_replace-value-..."><code>replace(to_replace, value, ...)</code></h4>
<ul>
<li>The  <code>to_replace</code>  parameter contains the value or the list of values  <strong>to be replaced</strong>. It can be a list of integers, strings, booleans, etc.</li>
<li>The  <code>value</code>  parameter contains the value or the list of the substitute  <strong>values</strong>. It can also be a list of integers, strings, booleans, etc.</li>
</ul>
<p>The <strong><code>replace</code></strong> method allows to <strong>replace</strong> one or more <strong>values</strong> ​​of a column of a<code>DataFrame</code>.</p>
<p><strong>BSP:</strong></p>
<pre class=" language-py"><code class="prism  language-py">df <span class="token operator">=</span> df<span class="token punctuation">.</span>replace<span class="token punctuation">(</span>to_replace <span class="token operator">=</span> <span class="token punctuation">[</span><span class="token string">'old_value1'</span><span class="token punctuation">,</span> <span class="token string">'old_value2'</span><span class="token punctuation">]</span><span class="token punctuation">,</span> value <span class="token operator">=</span> <span class="token punctuation">[</span><span class="token string">'new_value1'</span><span class="token punctuation">,</span> <span class="token string">'new_value'</span><span class="token punctuation">]</span><span class="token punctuation">)</span>
</code></pre>
<h4 id="rename..."><code>rename(...)</code></h4>
<p>This is possible thanks to the <strong><code>rename</code></strong> method which takes as argument a <strong>dictionary</strong> whose <strong>keys</strong> are the <strong>old</strong> names and the <strong>values</strong> are the <strong>new</strong> names<br>
<strong>BSP:</strong></p>
<pre class=" language-py"><code class="prism  language-py"><span class="token comment"># Rename column names, for renaming rows use default axis = 0</span>
df <span class="token operator">=</span> df<span class="token punctuation">.</span>rename<span class="token punctuation">(</span><span class="token punctuation">{</span><span class="token string">'old_name1'</span><span class="token punctuation">:</span> <span class="token string">'new_name1'</span><span class="token punctuation">,</span><span class="token string">'old_name2'</span><span class="token punctuation">:</span> <span class="token string">'new_name2'</span><span class="token punctuation">}</span><span class="token punctuation">,</span> axis <span class="token operator">=</span> <span class="token number">1</span><span class="token punctuation">)</span>
</code></pre>
<h4 id="astype..."><code>astype(...)</code></h4>
<p>As for the <strong><code>rename</code></strong> method, <strong><code>astype</code></strong> can take as argument a dictionary whose <strong>keys</strong> are the <strong>names of the columns whose type should be modified</strong> and the <strong>values</strong> are the <strong>new types</strong> to assign.</p>
<p><strong>BSP:</strong></p>
<pre class=" language-python"><code class="prism  language-python"><span class="token comment"># Method 1: Creation of a dictionary then call to the astype method of the DataFrame</span>
df <span class="token operator">=</span> df<span class="token punctuation">.</span>astype<span class="token punctuation">(</span><span class="token punctuation">{</span><span class="token string">'col_1'</span><span class="token punctuation">:</span> <span class="token string">'int'</span><span class="token punctuation">,</span> <span class="token string">'col_2'</span><span class="token punctuation">:</span> <span class="token string">'float'</span><span class="token punctuation">}</span><span class="token punctuation">)</span>

<span class="token comment"># Method 2: Selection of the column and then calling the astype method of a Series</span>
df<span class="token punctuation">[</span><span class="token string">'col_1'</span><span class="token punctuation">]</span> <span class="token operator">=</span> df<span class="token punctuation">[</span><span class="token string">'col_1'</span><span class="token punctuation">]</span><span class="token punctuation">.</span>astype<span class="token punctuation">(</span><span class="token string">'int'</span><span class="token punctuation">)</span>
</code></pre>
<h3 id="operations-on-the-values-​​of-a--dataframe--apply--method-and--lambda--functions">Operations on the values ​​of a  <code>DataFrame</code>  (<code>apply</code>  method and  <code>lambda</code>  functions)</h3>
<h4 id="applyfunc-axis-..."><code>apply(func, axis, ...)</code></h4>
<ul>
<li><strong><code>func</code></strong>  is the function to apply to the column.</li>
<li><strong><code>axis</code></strong>  is the dimension on which the operation must be applied.</li>
</ul>
<p><strong>BSP:</strong></p>
<pre class=" language-py"><code class="prism  language-py"><span class="token comment"># Sum of the ROWS for each column of df -&gt; one row, df.shape[1] columns</span>
df_lines <span class="token operator">=</span> df<span class="token punctuation">.</span><span class="token builtin">apply</span><span class="token punctuation">(</span>np<span class="token punctuation">.</span><span class="token builtin">sum</span><span class="token punctuation">,</span> axis <span class="token operator">=</span> <span class="token number">0</span><span class="token punctuation">)</span>

<span class="token comment"># Sum of columns for each ROW of df -&gt; one column, df.shape[0] rows</span>
df_columns <span class="token operator">=</span> df<span class="token punctuation">.</span><span class="token builtin">apply</span><span class="token punctuation">(</span>np<span class="token punctuation">.</span><span class="token builtin">sum</span><span class="token punctuation">,</span> axis <span class="token operator">=</span> <span class="token number">1</span><span class="token punctuation">)</span>
</code></pre>
<h3 id="dealing-with-missing-values">Dealing with missing values</h3>
<h4 id="isna-isnull"><code>isna(), isnull()</code></h4>
<p>The  <strong><code>isna</code></strong>  method of a  <code>DataFrame</code>  detects its missing values. This method does not take any arguments.<br>
This method returns the same  <code>DataFrame</code>  whose values are:</p>
<ul>
<li><strong><code>True</code></strong>  if the original table cell is a missing value (<code>np.nan</code>)</li>
<li><strong><code>False</code></strong>  otherwise.</li>
</ul>
<p>Since the  <code>isna</code>  method returns a  <code>DataFrame</code>, we can use it with other methods of the  <code>DataFrame</code>  class to get more precise information:</p>
<ul>
<li>The  <strong><code>any</code></strong>  method - thanks to its  <code>axis</code>  argument - allows to determine  <strong>which columns</strong>  (<code>axis = 0</code>) or  <strong>which rows</strong>  (<code>axis = 1</code>) contain at least one missing value.</li>
<li>The  <strong><code>sum</code></strong>  method counts the number of missing values per column or row (by specifying the  <code>axis</code>  argument). It is possible to use other statistical methods like  <code>mean</code>,<code>max</code>,  <code>argmax</code>, etc.</li>
</ul>
<p>The methods <code>isna</code>and <code>isnull</code>have exactly the same behavior.</p>
<p><strong>BSP:</strong></p>
<pre class=" language-python"><code class="prism  language-python"><span class="token comment"># COLUMNS containing at least one missing value are detected</span>
df<span class="token punctuation">.</span>isna<span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">.</span><span class="token builtin">any</span><span class="token punctuation">(</span>axis <span class="token operator">=</span> <span class="token number">0</span><span class="token punctuation">)</span>
<span class="token operator">&gt;&gt;</span><span class="token operator">&gt;</span> Name     <span class="token boolean">True</span>
<span class="token operator">&gt;&gt;</span><span class="token operator">&gt;</span> Country  <span class="token boolean">False</span>
<span class="token operator">&gt;&gt;</span><span class="token operator">&gt;</span> Age      <span class="token boolean">True</span>

<span class="token comment"># ROWS containing at least one missing value are detected</span>
df<span class="token punctuation">.</span>isna<span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">.</span><span class="token builtin">any</span> <span class="token punctuation">(</span>axis <span class="token operator">=</span> <span class="token number">1</span><span class="token punctuation">)</span>
<span class="token operator">&gt;&gt;</span><span class="token operator">&gt;</span> <span class="token number">0</span>    <span class="token boolean">True</span>
<span class="token operator">&gt;&gt;</span><span class="token operator">&gt;</span> <span class="token number">1</span>    <span class="token boolean">False</span>
<span class="token operator">&gt;&gt;</span><span class="token operator">&gt;</span> <span class="token number">2</span>    <span class="token boolean">False</span>

<span class="token comment"># We count the number of missing values for each COLUMN</span>
df<span class="token punctuation">.</span>isnull<span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">.</span><span class="token builtin">sum</span><span class="token punctuation">(</span>axis <span class="token operator">=</span> <span class="token number">0</span><span class="token punctuation">)</span>

<span class="token operator">&gt;&gt;</span><span class="token operator">&gt;</span> Name     <span class="token number">1</span>
<span class="token operator">&gt;&gt;</span><span class="token operator">&gt;</span> Country  <span class="token number">0</span>
<span class="token operator">&gt;&gt;</span><span class="token operator">&gt;</span> Age      <span class="token number">1</span>

<span class="token comment"># Count the number of missing values for each ROW</span>
df<span class="token punctuation">.</span>isnull<span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">.</span><span class="token builtin">sum</span><span class="token punctuation">(</span>axis <span class="token operator">=</span> <span class="token number">1</span><span class="token punctuation">)</span>
<span class="token operator">&gt;&gt;</span><span class="token operator">&gt;</span> <span class="token number">0</span>   <span class="token number">2</span>
<span class="token operator">&gt;&gt;</span><span class="token operator">&gt;</span> <span class="token number">1</span>   <span class="token number">0</span>
<span class="token operator">&gt;&gt;</span><span class="token operator">&gt;</span> <span class="token number">2</span>   <span class="token number">0</span>
</code></pre>
<h4 id="fillnavalue"><code>fillna(value)</code></h4>
<p>The <code>fillna</code> method allows you to replace the missing values of a <code>DataFrame</code> by <strong>values you want</strong>.<br>
To avoid making replacement errors, it is very important to <strong>select the correct columns</strong> before using the <code>fillna</code> method.<br>
It is common to replace missing values of a column containing  <strong>numerical</strong>  values with  <strong>statistics</strong>  like:</p>
<ul>
<li>The  <strong>mean</strong>:  <code>.mean</code></li>
<li>The  <strong>median</strong>:  <code>.median</code></li>
<li>The  <strong>minimum / maximum</strong>:  <code>.min</code>  /  <code>.max</code>.</li>
</ul>
<p>For categorical type columns, replace the missing values with:</p>
<ul>
<li>The  <strong>mode</strong>, i.e. the most frequent modality:  <code>.mode</code>. <strong>Achtung, <code>mode()[0]</code> verwenden !!!</strong></li>
<li>A  <strong>constant</strong>  or arbitrary category:  <code>0</code>,<code>-1</code>.</li>
</ul>
<p><strong>BSP:</strong></p>
<pre class=" language-python"><code class="prism  language-python"><span class="token comment"># We replace all the NaNs of the DataFrame by zeros</span>
df<span class="token punctuation">.</span>fillna<span class="token punctuation">(</span><span class="token number">0</span><span class="token punctuation">)</span>

<span class="token comment"># We replace the NaNs of each numerical column by the average on this column </span>
<span class="token comment"># mean() wird für jede Spalte seperat berechnet und ersetzt !!!</span>
df<span class="token punctuation">.</span>fillna<span class="token punctuation">(</span>df<span class="token punctuation">.</span>mean<span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">)</span> 
</code></pre>
<h4 id="dropnaaxis-how-subset-.."><code>dropna(axis, how, subset, ..)</code></h4>
<ul>
<li>The  <strong><code>axis</code></strong>  parameter specifies whether to delete rows or columns (<strong><code>0</code></strong>  for rows,  <strong><code>1</code></strong>  for columns).</li>
<li>The  <strong><code>how</code></strong>  parameter lets you specify how the rows (or columns) are deleted:
<ul>
<li><strong><code>how = 'any'</code></strong>: We delete the row (or column) if it contains  <strong>at least one</strong>  missing value.</li>
<li><strong><code>how = 'all'</code></strong>: We delete the row (or column) if it contains  <strong>only</strong>  missing values.</li>
</ul>
</li>
<li>The  <strong><code>subset</code></strong>  parameter is used to specify the columns/rows on which the search for missing values is carried out.</li>
</ul>
<p><strong>BSP:</strong></p>
<pre class=" language-python"><code class="prism  language-python"><span class="token comment"># We delete all the rows containing at least one missing value</span>
df <span class="token operator">=</span> df<span class="token punctuation">.</span>dropna<span class="token punctuation">(</span>axis <span class="token operator">=</span> <span class="token number">0</span><span class="token punctuation">,</span> how <span class="token operator">=</span> <span class="token string">'any'</span><span class="token punctuation">)</span>

<span class="token comment"># We delete the empty columns</span>
df <span class="token operator">=</span> df<span class="token punctuation">.</span>dropna<span class="token punctuation">(</span>axis <span class="token operator">=</span> <span class="token number">1</span><span class="token punctuation">,</span> how <span class="token operator">=</span> <span class="token string">'all'</span><span class="token punctuation">)</span>

<span class="token comment"># We remove the rows with missing values in the 3 columns 'col2', 'col3' and 'col4'</span>
df<span class="token punctuation">.</span>dropna<span class="token punctuation">(</span>axis <span class="token operator">=</span> <span class="token number">0</span><span class="token punctuation">,</span> how <span class="token operator">=</span> <span class="token string">'all'</span><span class="token punctuation">,</span> subset <span class="token operator">=</span> <span class="token punctuation">[</span><span class="token string">'col2'</span><span class="token punctuation">,</span> <span class="token string">'col3'</span><span class="token punctuation">,</span> <span class="token string">'col4'</span><span class="token punctuation">]</span><span class="token punctuation">)</span>
</code></pre>
<h2 id="filtering-merging-ordering-and-grouping">Filtering, merging, ordering and grouping</h2>
<h4 id="filtering-a-dataframe-with-binary-operators">Filtering a DataFrame with binary operators</h4>
<pre class=" language-python"><code class="prism  language-python">   The <span class="token string">'and'</span> operator<span class="token punctuation">:</span>  `<span class="token operator">&amp;</span>`
   The <span class="token string">'or'</span> operator<span class="token punctuation">:</span>  `<span class="token operator">|</span>`
   The <span class="token string">'not'</span> operator<span class="token punctuation">:</span>  `<span class="token operator">-</span>`
</code></pre>
<p>The conditions must be written <strong>between parentheses</strong> to eliminate any ambiguity on the <strong>order of evaluation</strong> of the conditions.</p>
<p><strong>BSP:</strong></p>
<pre class=" language-python"><code class="prism  language-python"><span class="token comment"># Filtering of the DataFrame on the 2 previous conditions</span>
<span class="token keyword">print</span><span class="token punctuation">(</span>df<span class="token punctuation">[</span><span class="token punctuation">(</span>df<span class="token punctuation">[</span><span class="token string">'year'</span><span class="token punctuation">]</span> <span class="token operator">==</span> <span class="token number">1979</span><span class="token punctuation">)</span> <span class="token operator">&amp;</span> <span class="token punctuation">(</span>df<span class="token punctuation">[</span><span class="token string">'surface'</span><span class="token punctuation">]</span><span class="token operator">&gt;</span> <span class="token number">60</span><span class="token punctuation">)</span><span class="token punctuation">]</span><span class="token punctuation">)</span>

<span class="token comment"># Filtering of the DataFrame on the the negation of a condition</span>
<span class="token keyword">print</span><span class="token punctuation">(</span>df<span class="token punctuation">[</span><span class="token operator">-</span><span class="token punctuation">(</span>df<span class="token punctuation">[</span><span class="token string">'district'</span><span class="token punctuation">]</span> <span class="token operator">==</span> <span class="token string">'Bercy'</span><span class="token punctuation">)</span><span class="token punctuation">]</span><span class="token punctuation">)</span>
</code></pre>
<h4 id="pandas.concatobjs-axis-..."><code>pandas.concat(objs, axis, ...)</code></h4>
<p>The <code>concat</code> function from the <code>pandas</code> module enables the concatenation of multiple <code>DataFrames</code>, either by stacking them vertically or by aligning them side by side.</p>
<ul>
<li>The  <code>objs</code>  parameter takes a list of  <code>DataFrames</code>  to concatenate.</li>
<li>The  <code>axis</code>  parameter specifies whether the concatenation should be vertical (<code>axis = 0</code>) or horizontal (<code>axis = 1</code>).</li>
</ul>
<p>When the number of rows or columns of the <code>DataFrames</code> does not match, the<code>concat</code> function fills the empty cells with <code>NaN</code>.</p>
<p><strong>BSP:</strong></p>
<pre class=" language-python"><code class="prism  language-python"><span class="token comment"># Spalten zweier DataFrames zusammenfügen</span>
union <span class="token operator">=</span> pd<span class="token punctuation">.</span>concat<span class="token punctuation">(</span><span class="token punctuation">[</span>df1<span class="token punctuation">,</span> df2<span class="token punctuation">]</span><span class="token punctuation">,</span> axis<span class="token operator">=</span><span class="token number">1</span><span class="token punctuation">)</span>
</code></pre>
<h4 id="mergeright-on-how-..."><code>merge(right, on, how, ...)</code></h4>
<ul>
<li>The  <strong><code>right</code></strong>  parameter represents the  <code>DataFrame</code>  to be merged with the one calling the method.</li>
<li>The  <strong><code>on</code></strong>  parameter specifies the names of the columns in both  <code>DataFrames</code>  that will serve as references for the merge. These columns must be shared between the two.</li>
<li>The  <strong><code>how</code></strong>  parameter lets you choose the type of join to perform when merging the  <code>DataFrames</code>. The available values for this parameter are based on SQL-style joins: <code>'inner'</code>, <code>'outer'</code>, <code>'left'</code>, or <code>'right'</code></li>
</ul>
<p><strong>BSP:</strong></p>
<pre class=" language-python"><code class="prism  language-python">Persons<span class="token punctuation">.</span>merge<span class="token punctuation">(</span>right <span class="token operator">=</span> Vehicles<span class="token punctuation">,</span> on <span class="token operator">=</span> <span class="token string">'Car'</span><span class="token punctuation">,</span> how <span class="token operator">=</span> <span class="token string">'left'</span><span class="token punctuation">)</span>
</code></pre>
<h4 id="set_indexargument"><code>set_index(argument)</code></h4>
<p>This method can take as argument:</p>
<ul>
<li>The  <strong>name</strong>  of a column to use as indexing.</li>
<li>A  <code>numpy</code>  <code>array</code>  or  <code>pandas</code>  <code>Series</code>  with the same number of rows as the  <code>DataFrame</code>  calling the method.</li>
</ul>
<p>The index of a <code>DataFrame</code> can be retrieved using its <code>.index</code> attribute</p>
<p><strong>BSP:</strong></p>
<pre class=" language-python"><code class="prism  language-python"><span class="token comment"># New index to use</span>
new_index <span class="token operator">=</span> <span class="token punctuation">[</span><span class="token string">'10000'</span> <span class="token operator">+</span> <span class="token builtin">str</span><span class="token punctuation">(</span>i<span class="token punctuation">)</span> <span class="token keyword">for</span> i <span class="token keyword">in</span> <span class="token builtin">range</span><span class="token punctuation">(</span><span class="token number">6</span><span class="token punctuation">)</span><span class="token punctuation">]</span>

<span class="token comment"># Using an array or a Series is equivalent</span>
index_array <span class="token operator">=</span> np<span class="token punctuation">.</span>array<span class="token punctuation">(</span>new_index<span class="token punctuation">)</span>
index_series <span class="token operator">=</span> pd<span class="token punctuation">.</span>Series<span class="token punctuation">(</span>new_index<span class="token punctuation">)</span>


df <span class="token operator">=</span> df<span class="token punctuation">.</span>set_index<span class="token punctuation">(</span>index_array<span class="token punctuation">)</span>
df <span class="token operator">=</span> df<span class="token punctuation">.</span>set_index<span class="token punctuation">(</span>index_series<span class="token punctuation">)</span>
</code></pre>
<h4 id="sort_valuesby-ascending-..."><code>sort_values(by, ascending, ...)</code></h4>
<ul>
<li>
<p>The  <code>by</code>  parameter allows you to specify on which column(s) the sort is performed.</p>
</li>
<li>
<p>The  <code>ascending</code>  parameter is a boolean value (<code>True</code>  or  <code>False</code>) determining whether the sorting order is ascending or descending. By default this parameter is set to  <code>True</code>.</p>
</li>
</ul>
<p><strong>BSP:</strong></p>
<pre class=" language-python"><code class="prism  language-python"><span class="token comment"># We first sort the DataFrame df by the column 'Bonus Points' </span>
<span class="token comment"># then in case of equality, by the column 'Grade'.</span>
df_sorted <span class="token operator">=</span> df<span class="token punctuation">.</span>sort_values<span class="token punctuation">(</span>by <span class="token operator">=</span> <span class="token punctuation">[</span><span class="token string">'Bonus Points'</span><span class="token punctuation">,</span> <span class="token string">'Grade'</span><span class="token punctuation">]</span><span class="token punctuation">,</span> ascending <span class="token operator">=</span> <span class="token boolean">True</span><span class="token punctuation">)</span>
</code></pre>
<h4 id="sort_index"><code>sort_index</code></h4>
<p>is used to sort a  <code>DataFrame</code>  based on its index.</p>
<p>When the index is the default numerical one, this method may not offer significant advantages. However, it can frequently be utilized in conjunction with the  <code>set_index</code>  method of a  <code>DataFrame</code>, as we’ve recently covered.</p>
<p><strong>BSP:</strong></p>
<pre class=" language-py"><code class="prism  language-py"><span class="token comment"># We define the column 'Grade' as the index of df</span>
df <span class="token operator">=</span> df<span class="token punctuation">.</span>set_index<span class="token punctuation">(</span><span class="token string">'Grade'</span><span class="token punctuation">)</span>

<span class="token comment"># We sort the DataFrame df according to its index</span>
df <span class="token operator">=</span> df<span class="token punctuation">.</span>sort_index<span class="token punctuation">(</span><span class="token punctuation">)</span>
</code></pre>
<h3 id="grouping-the-elements-of-a--dataframe">Grouping the elements of a  <code>DataFrame</code></h3>
<p>The  <strong><code>groupby</code></strong>  method allows you to  <strong>group the rows</strong>  of a  <code>DataFrame</code>  which share a  <strong>common</strong>  value on a given column.</p>
<p><strong>This method does not return a  <code>DataFrame</code>.</strong>  The object returned by the  <code>groupby</code>  method is an object of the  **<code>DataFrameGroupBy</code>**class.</p>
<p>This class is used to perform operations such as calculating statistics (sum, average, maximum, etc.) for each category of the column on which the rows are grouped.</p>
<p>The general structure of a  <strong><code>groupby</code>  operation</strong>  is as follows:</p>
<ul>
<li><strong>Split</strong>  the data.</li>
<li><strong>Apply</strong>  a function.</li>
<li><strong>Combine</strong>  the results.</li>
</ul>
<p>All the usual statistical methods (<code>count</code>,<code>mean</code>,  <code>max</code>, etc.) can be used as a suffix of the  <code>groupby</code>  method. These will only be applied on columns of compatible type.</p>
<p>For each column, you can specify which function should be used in the  <strong>Apply</strong>  step of a  <code>groupby</code>  operation. To do this, we use the  **<code>agg</code>**method of the  <code>DataFrameGroupBy</code>  class. This involves providing a  <strong>dictionary</strong>  where each  <strong>key</strong>  represents the  <strong>name</strong>  of a column, and the corresponding  <strong>value</strong>  indicates the  <strong>function</strong>  to be applied.</p>
<p><strong>BSP:</strong></p>
<pre class=" language-python"><code class="prism  language-python">n_categories <span class="token operator">=</span> <span class="token keyword">lambda</span> store_type<span class="token punctuation">:</span> <span class="token builtin">len</span><span class="token punctuation">(</span>np<span class="token punctuation">.</span>unique<span class="token punctuation">(</span>store_type<span class="token punctuation">)</span><span class="token punctuation">)</span>
<span class="token comment"># Achtung, der Name der Spalte wird so übergeben (nicht als String)</span>

functions_to_apply <span class="token operator">=</span> <span class="token punctuation">{</span>
<span class="token comment"># Classic statistical methods can be entered with</span>
<span class="token comment"># strings</span>
<span class="token string">'total_amt'</span><span class="token punctuation">:</span> <span class="token punctuation">[</span><span class="token string">'min'</span><span class="token punctuation">,</span> <span class="token string">'max'</span><span class="token punctuation">,</span> <span class="token string">'sum'</span><span class="token punctuation">]</span><span class="token punctuation">,</span>
<span class="token string">'store_type'</span><span class="token punctuation">:</span> n_categories
<span class="token punctuation">}</span>

transactions<span class="token punctuation">.</span>groupby<span class="token punctuation">(</span><span class="token string">'cust_id'</span><span class="token punctuation">)</span><span class="token punctuation">.</span>agg<span class="token punctuation">(</span>functions_to_apply<span class="token punctuation">)</span>
</code></pre>
<h3 id="crosstabclo1-col2-normalize--0-1"><code>crosstab(clo1, col2, [normalize = 0| 1])</code></h3>
<p>A crosstab allows us to visualize the <strong>appearance frequency</strong> of <strong>pairs of categories</strong> in a <code>DataFrame</code>.<br>
The  <strong><code>normalize</code></strong>  argument of  <code>crosstab</code>  allows to display frequencies as a percentage.<br>
Thus, the argument  <strong><code>normalize = 1</code></strong>  normalizes the table over the axis 1 of the crosstab, i.e. its  <strong>columns</strong>.<br>
Conversely, by entering the argument <strong><code>normalize = 0</code></strong>, the crosstab is normalized over each <strong>row</strong>.</p>
<p><strong>BSP:</strong></p>
<pre class=" language-python"><code class="prism  language-python"><span class="token comment">#We recover the year of the transaction.</span>
column1 <span class="token operator">=</span> transactions<span class="token punctuation">[</span><span class="token string">'tran_date'</span><span class="token punctuation">]</span><span class="token punctuation">.</span><span class="token builtin">apply</span><span class="token punctuation">(</span><span class="token keyword">lambda</span> x<span class="token punctuation">:</span> x<span class="token punctuation">.</span>split<span class="token punctuation">(</span><span class="token string">'-'</span><span class="token punctuation">)</span><span class="token punctuation">[</span><span class="token number">2</span><span class="token punctuation">]</span><span class="token punctuation">)</span><span class="token punctuation">.</span>astype<span class="token punctuation">(</span><span class="token builtin">int</span><span class="token punctuation">)</span>

column2 <span class="token operator">=</span> transactions<span class="token punctuation">[</span><span class="token string">'store_type'</span><span class="token punctuation">]</span>

pd<span class="token punctuation">.</span>crosstab<span class="token punctuation">(</span>column1<span class="token punctuation">,</span>
            column2<span class="token punctuation">,</span>
            normalize <span class="token operator">=</span> <span class="token number">1</span><span class="token punctuation">)</span>
</code></pre>

