---


---

<h3 id="beispiel-code-wallet.py">Beispiel Code: <a href="http://Wallet.py">Wallet.py</a></h3>
<pre class=" language-python"><code class="prism  language-python"><span class="token keyword">class</span>  <span class="token class-name">InsufficientAmount</span><span class="token punctuation">(</span>Exception<span class="token punctuation">)</span><span class="token punctuation">:</span>
	<span class="token keyword">def</span>  <span class="token function">__init__</span><span class="token punctuation">(</span>self<span class="token punctuation">,</span> <span class="token operator">*</span>args<span class="token punctuation">:</span> <span class="token builtin">object</span><span class="token punctuation">)</span> <span class="token operator">-</span><span class="token operator">&gt;</span> <span class="token boolean">None</span><span class="token punctuation">:</span>
		<span class="token builtin">super</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">.</span>__init__<span class="token punctuation">(</span><span class="token operator">*</span>args<span class="token punctuation">)</span>

<span class="token keyword">class</span>  <span class="token class-name">NegativeAmount</span><span class="token punctuation">(</span>Exception<span class="token punctuation">)</span><span class="token punctuation">:</span>
	<span class="token keyword">def</span>  <span class="token function">__init__</span><span class="token punctuation">(</span>self<span class="token punctuation">,</span> <span class="token operator">*</span>args<span class="token punctuation">:</span> <span class="token builtin">object</span><span class="token punctuation">)</span> <span class="token operator">-</span><span class="token operator">&gt;</span> <span class="token boolean">None</span><span class="token punctuation">:</span>
		<span class="token builtin">super</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">.</span>__init__<span class="token punctuation">(</span><span class="token operator">*</span>args<span class="token punctuation">)</span>
		
<span class="token keyword">class</span>  <span class="token class-name">Wallet</span><span class="token punctuation">:</span>
	<span class="token keyword">def</span>  <span class="token function">__init__</span><span class="token punctuation">(</span>self<span class="token punctuation">,</span> contribution<span class="token punctuation">:</span> <span class="token builtin">float</span>  <span class="token operator">=</span>  <span class="token number">0</span> <span class="token punctuation">)</span> <span class="token operator">-</span><span class="token operator">&gt;</span> <span class="token boolean">None</span><span class="token punctuation">:</span>
	<span class="token keyword">if</span>  contribution  <span class="token operator">&lt;</span>  <span class="token number">0</span><span class="token punctuation">:</span>
		<span class="token keyword">raise</span>  NegativeAmount
	self<span class="token punctuation">.</span>balance <span class="token punctuation">:</span> <span class="token builtin">float</span>  <span class="token operator">=</span>  contribution

<span class="token keyword">def</span>  <span class="token function">add_cash</span><span class="token punctuation">(</span>self<span class="token punctuation">,</span> cash_to_add<span class="token punctuation">:</span> <span class="token builtin">float</span><span class="token punctuation">)</span> <span class="token operator">-</span><span class="token operator">&gt;</span> <span class="token boolean">None</span><span class="token punctuation">:</span>
	<span class="token keyword">if</span>  cash_to_add  <span class="token operator">&lt;</span>  <span class="token number">0</span><span class="token punctuation">:</span>
		<span class="token keyword">raise</span>  NegativeAmount
	<span class="token keyword">if</span>  cash_to_add  <span class="token operator">&gt;</span>  <span class="token number">0</span><span class="token punctuation">:</span>
		self<span class="token punctuation">.</span>balance  <span class="token operator">+=</span>  cash_to_add
	<span class="token keyword">return</span>  self<span class="token punctuation">.</span>balance

<span class="token keyword">def</span>  <span class="token function">spend_cash</span><span class="token punctuation">(</span>self<span class="token punctuation">,</span> cash_to_spend<span class="token punctuation">:</span> <span class="token builtin">float</span><span class="token punctuation">)</span> <span class="token operator">-</span><span class="token operator">&gt;</span> <span class="token boolean">None</span><span class="token punctuation">:</span>
	<span class="token keyword">if</span>  cash_to_spend  <span class="token operator">&lt;</span>  <span class="token number">0</span><span class="token punctuation">:</span>
		<span class="token keyword">raise</span>  NegativeAmount
	<span class="token keyword">if</span>  self<span class="token punctuation">.</span>balance  <span class="token operator">-</span>  cash_to_spend  <span class="token operator">&lt;</span>  <span class="token number">0</span><span class="token punctuation">:</span>
		<span class="token keyword">raise</span>  InsufficientAmount
	<span class="token keyword">else</span><span class="token punctuation">:</span>
		self<span class="token punctuation">.</span>balance  <span class="token operator">-=</span>  cash_to_spend
	<span class="token keyword">return</span>  self<span class="token punctuation">.</span>balance
</code></pre>
<h3 id="pytest-test_wallet.py">Pytest: test_Wallet.py</h3>
<pre class=" language-python"><code class="prism  language-python"><span class="token keyword">import</span>  pytest
<span class="token keyword">from</span>  Wallet  <span class="token keyword">import</span>  Wallet<span class="token punctuation">,</span> InsufficientAmount<span class="token punctuation">,</span> NegativeAmount

@pytest<span class="token punctuation">.</span>fixture
<span class="token keyword">def</span>  <span class="token function">empty_wallet</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">:</span>
	<span class="token keyword">return</span>  Wallet<span class="token punctuation">(</span><span class="token punctuation">)</span>

@pytest<span class="token punctuation">.</span>fixture
<span class="token keyword">def</span>  <span class="token function">wallet20</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">:</span>
	<span class="token keyword">return</span>  Wallet<span class="token punctuation">(</span><span class="token number">20</span><span class="token punctuation">)</span>

<span class="token keyword">def</span>  <span class="token function">test_empty_wallet</span><span class="token punctuation">(</span>empty_wallet<span class="token punctuation">)</span><span class="token punctuation">:</span>
	<span class="token keyword">assert</span>  empty_wallet<span class="token punctuation">.</span>balance <span class="token operator">==</span>  <span class="token number">0</span>

<span class="token keyword">def</span>  <span class="token function">test_filled_wallet</span><span class="token punctuation">(</span>wallet20<span class="token punctuation">)</span><span class="token punctuation">:</span>
	<span class="token keyword">assert</span>  wallet20<span class="token punctuation">.</span>balance <span class="token operator">==</span>  <span class="token number">20</span>

@pytest<span class="token punctuation">.</span>mark<span class="token punctuation">.</span>parametrize<span class="token punctuation">(</span><span class="token string">"earned, spent, expected"</span><span class="token punctuation">,</span> <span class="token punctuation">[</span><span class="token punctuation">(</span><span class="token number">100</span><span class="token punctuation">,</span> <span class="token number">100</span><span class="token punctuation">,</span> <span class="token number">0</span><span class="token punctuation">)</span><span class="token punctuation">,</span> <span class="token punctuation">(</span><span class="token number">20</span><span class="token punctuation">,</span> <span class="token number">0</span><span class="token punctuation">,</span> <span class="token number">20</span><span class="token punctuation">)</span><span class="token punctuation">,</span> <span class="token punctuation">(</span><span class="token number">10</span><span class="token punctuation">,</span> <span class="token number">10</span><span class="token punctuation">,</span> <span class="token number">0</span><span class="token punctuation">)</span><span class="token punctuation">]</span><span class="token punctuation">)</span>
<span class="token keyword">def</span>  <span class="token function">test_empty_transaction</span><span class="token punctuation">(</span>empty_wallet<span class="token punctuation">,</span> earned<span class="token punctuation">,</span> spent<span class="token punctuation">,</span> expected<span class="token punctuation">)</span><span class="token punctuation">:</span>

	empty_wallet<span class="token punctuation">.</span>add_cash<span class="token punctuation">(</span>earned<span class="token punctuation">)</span>
	empty_wallet<span class="token punctuation">.</span>spend_cash<span class="token punctuation">(</span>spent<span class="token punctuation">)</span>
	<span class="token keyword">assert</span>  empty_wallet<span class="token punctuation">.</span>balance <span class="token operator">==</span>  expected

@pytest<span class="token punctuation">.</span>mark<span class="token punctuation">.</span>parametrize<span class="token punctuation">(</span><span class="token string">"earned, spent, expected"</span><span class="token punctuation">,</span> <span class="token punctuation">[</span><span class="token punctuation">(</span><span class="token number">100</span><span class="token punctuation">,</span> <span class="token number">100</span><span class="token punctuation">,</span> <span class="token number">20</span><span class="token punctuation">)</span><span class="token punctuation">,</span> <span class="token punctuation">(</span><span class="token number">20</span><span class="token punctuation">,</span> <span class="token number">0</span><span class="token punctuation">,</span> <span class="token number">40</span><span class="token punctuation">)</span><span class="token punctuation">,</span> <span class="token punctuation">(</span><span class="token number">10</span><span class="token punctuation">,</span> <span class="token number">10</span><span class="token punctuation">,</span> <span class="token number">20</span><span class="token punctuation">)</span><span class="token punctuation">]</span><span class="token punctuation">)</span>
<span class="token keyword">def</span>  <span class="token function">test_filled_transactions</span><span class="token punctuation">(</span>wallet20<span class="token punctuation">,</span> earned<span class="token punctuation">,</span> spent<span class="token punctuation">,</span> expected<span class="token punctuation">)</span><span class="token punctuation">:</span>
	
	wallet20<span class="token punctuation">.</span>add_cash<span class="token punctuation">(</span>earned<span class="token punctuation">)</span>
	wallet20<span class="token punctuation">.</span>spend_cash<span class="token punctuation">(</span>spent<span class="token punctuation">)</span>
	<span class="token keyword">assert</span>  wallet20<span class="token punctuation">.</span>balance <span class="token operator">==</span>  expected

<span class="token keyword">def</span>  <span class="token function">test_Exceptions</span><span class="token punctuation">(</span>empty_wallet<span class="token punctuation">,</span> wallet20<span class="token punctuation">)</span><span class="token punctuation">:</span>
	
	<span class="token keyword">with</span>  pytest<span class="token punctuation">.</span>raises<span class="token punctuation">(</span>InsufficientAmount<span class="token punctuation">)</span><span class="token punctuation">:</span>
		empty_wallet<span class="token punctuation">.</span>spend_cash<span class="token punctuation">(</span><span class="token number">1</span><span class="token punctuation">)</span>
	
	<span class="token keyword">with</span>  pytest<span class="token punctuation">.</span>raises<span class="token punctuation">(</span>InsufficientAmount<span class="token punctuation">)</span><span class="token punctuation">:</span>
		wallet20<span class="token punctuation">.</span>spend_cash<span class="token punctuation">(</span><span class="token number">21</span><span class="token punctuation">)</span>
	
	<span class="token keyword">with</span>  pytest<span class="token punctuation">.</span>raises<span class="token punctuation">(</span>NegativeAmount<span class="token punctuation">)</span><span class="token punctuation">:</span>
		wallet20<span class="token punctuation">.</span>add_cash<span class="token punctuation">(</span><span class="token operator">-</span><span class="token number">1</span><span class="token punctuation">)</span>
	
	<span class="token keyword">with</span>  pytest<span class="token punctuation">.</span>raises<span class="token punctuation">(</span>NegativeAmount<span class="token punctuation">)</span><span class="token punctuation">:</span>
		wallet20<span class="token punctuation">.</span>spend_cash<span class="token punctuation">(</span><span class="token operator">-</span><span class="token number">1</span><span class="token punctuation">)</span>
</code></pre>

