---


---

<h2 id="regression">Regression</h2>
<p><strong><code>X_train, X_test, y_train, y_test = train_test_split(X, y, test_size = 0.2, random_state = 42)</code></strong></p>
<ul>
<li>
<p><code>X_train</code>  and<code>y_train</code>  represent the explanatory and target variables of the  <strong>training</strong>  dataset.</p>
</li>
<li>
<p><code>X_test</code>  and<code>y_test</code>  signify the explanatory and target variables of the  <strong>test</strong>  dataset.</p>
</li>
<li>
<p>The  <code>test_size</code>  parameter dictates the  <strong>proportion</strong>  of the dataset allocated for the test set. In the example above, this proportion is set to 20% of the initial dataset.</p>
</li>
<li>
<p>The  <code>random_state</code>  argument ensures that the data splitting can be reproduced. Indeed, the operation being random, 2 successive cuts will in theory give 2 different results. As long as the value of  <code>random_state</code>  is the same (it doesn’t matter what value it is), the result of the train_test_split function will remain the same.</p>
</li>
</ul>
<p>The  <code>scikit-learn</code>  API makes it easy to train and evaluate models. All scikit-learn model classes have the following two methods:</p>
<ul>
<li>
<p><strong><code>fit</code></strong>: Train the model on the dataset given as input.</p>
</li>
<li>
<p><strong><code>predict</code></strong>: Make a prediction from a set of explanatory variables given as input.</p>
</li>
</ul>
<p>Below is an example of training a model with scikit-learn:</p>
<pre class=" language-python"><code class="prism  language-python"><span class="token comment"># Instantiation of the model</span>
linreg <span class="token operator">=</span> LinearRegression<span class="token punctuation">(</span><span class="token punctuation">)</span>

<span class="token comment"># Training the model on the training set</span>
linreg<span class="token punctuation">.</span>fit<span class="token punctuation">(</span>X_train<span class="token punctuation">,</span> y_train<span class="token punctuation">)</span>

<span class="token comment"># Prediction of the target variable for the test dataset. These predictions are stored in y_pred.</span>
y_pred <span class="token operator">=</span> linreg<span class="token punctuation">.</span>predict<span class="token punctuation">(</span>X_test<span class="token punctuation">)</span>
</code></pre>
<h4 id="evaluation">Evaluation</h4>
<p>To assess the accuracy of the model’s predictions, we have several predefined metrics available in the  <code>scikit-learn</code>  library. One commonly used metric for regression tasks is the Mean Squared Error (MSE). It is accessible through the  <code>mean_squared_error</code>function in the  <code>metrics</code>  submodule of  <code>scikit-learn</code>.</p>
<p>The MSE is computed by averaging the squared differences between the predicted values obtained from the regression function and the actual target values.</p>
<p>The  <code>mean_squared_error</code>  function of  <code>scikit-learn</code>  is used as follows:</p>
<pre class=" language-python"><code class="prism  language-python">   mean_squared_error<span class="token punctuation">(</span>y_true<span class="token punctuation">,</span> y_pred<span class="token punctuation">)</span>
</code></pre>
<p>where:</p>
<ul>
<li><code>y_true</code>  contains the true values of the target variable.</li>
<li><code>y_pred</code>  contains the values  <strong>predicted</strong>  by our model for the same explanatory variables.</li>
</ul>
<p>The Mean Squared Error (MSE) you’ll obtain is expected to be in the millions on the test data, which might be hard to interpret.</p>
<p>To address this, we’ll also utilize another metric called the  <strong>Mean Absolute Error</strong>  (MAE). This metric is on the same scale as the target variable, making it more easily interpretable.</p>
<h2 id="classification">Classification</h2>

