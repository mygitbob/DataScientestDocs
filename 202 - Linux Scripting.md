---


---

<p>nicht definierte Variablen sind leer</p>

<table>
<thead>
<tr>
<th>Variable</th>
<th>Bedeutung</th>
</tr>
</thead>
<tbody>
<tr>
<td><code>$0</code></td>
<td>name of the bash script (or -bash)</td>
</tr>
<tr>
<td><code>$1</code> - <code>$9</code></td>
<td>first 9 arguments</td>
</tr>
<tr>
<td><code>$#</code></td>
<td>how many args were passed</td>
</tr>
<tr>
<td><code>$@</code></td>
<td>all args</td>
</tr>
<tr>
<td><code>$?</code></td>
<td>exit status of most recently run process</td>
</tr>
<tr>
<td><code>$$</code></td>
<td>process id of the current script</td>
</tr>
<tr>
<td><code>$USER</code></td>
<td>username of the user running the script</td>
</tr>
<tr>
<td><code>$HOSTNAME</code></td>
<td>hostname of the machine running the script</td>
</tr>
<tr>
<td><code>$SECONDS</code></td>
<td>number of seconds since the script was started</td>
</tr>
<tr>
<td><code>$RANDOM</code></td>
<td>random number</td>
</tr>
<tr>
<td><code>$LINENO</code></td>
<td>current line number of the script</td>
</tr>
</tbody>
</table><p><code>set -- "Argument1" "Argument2" "Argument3" "Argument4" "Argument5"</code>  setzt die Positional Parameters in einem Bash-Skript neu.</p>
<h3 id="quotes">Quotes</h3>
<p><code>" ... "</code> substitution works<br>
<code>' ... '</code> removes special meaning of special characters<br>
<code>\</code> removes special meaning of next character</p>
<p>Mix both ways:</p>
<pre><code>VIRUS="covid" 
echo "Due to $VIRUS virus company have lost \$9 million"
</code></pre>
<h3 id="mathematische-ausdrücke">Mathematische Ausdrücke</h3>
<p><code>let "a = 2"</code><br>
<code>let "b = 6"</code><br>
<code>let "c = a * b"</code><br>
Ausgabe: <code>12</code></p>
<h3 id="exporting-variables">Exporting Variables</h3>
<p>Variables will be deleted when the current session ends. Each script starts as child shell when run. Exporting makes a Variable global for all child processes created by the current bash.<br>
locally <code>.bashrc</code> or <code>.profile</code>in home dir can save variables, add  <code>export VAR="blabla"</code><br>
globally in <code>/etc/profile</code><br>
local changes precedes global changes</p>
<h3 id="user-input">User Input</h3>
<pre><code>read -p &lt;message&gt; VAR_NAME			# -p for prompt
read -sp &lt;message&gt; HIDDEN_INPUT		# -sp for hidden input
</code></pre>
<h2 id="loops-and-conditions">Loops and conditions</h2>
<h3 id="if-then">IF THEN</h3>
<p><strong>Achtung</strong> nach <strong><code>[</code></strong> und <strong><code>]</code></strong> muss ein Leerzeichen sein</p>
<pre class=" language-bash"><code class="prism  language-bash">firstname<span class="token operator">=</span><span class="token string">"Diane
if [ <span class="token variable">$firstname</span> = "</span>Daniel<span class="token string">" ]
then
echo "</span>Hi Daniel<span class="token operator">!</span> <span class="token string">"
elif [ <span class="token variable">$firstname</span> = "</span>Diane<span class="token string">" ]
then
echo "</span>Hi Diane<span class="token string">"
else
echo "</span>Hello<span class="token string">" + <span class="token variable">$firstname</span> +"</span><span class="token operator">!</span>"
<span class="token keyword">fi</span>
</code></pre>

<table>
<thead>
<tr>
<th>Condition</th>
<th>Bedeutung</th>
</tr>
</thead>
<tbody>
<tr>
<td><code>$var1 = $var2</code></td>
<td>Test der character arrays auf Gleichheit</td>
</tr>
<tr>
<td><code>$var1 != $var2</code></td>
<td>Test der character arrays auf Ungleichheit</td>
</tr>
<tr>
<td><code>-z $var1</code></td>
<td>Test ob character arrays  <strong>leer</strong> ist</td>
</tr>
<tr>
<td><code>-n $var1</code></td>
<td>Test ob character arrays  nicht leer ist</td>
</tr>
<tr>
<td><code>$var1 -eq $var2</code></td>
<td>Test von nummerischen Werten auf Gleichheit</td>
</tr>
<tr>
<td><code>$var1 -ne $var2</code></td>
<td>Test von nummerischen Werten auf Ungleichheit</td>
</tr>
<tr>
<td><code>$var1 -lt | -gt | -le | -ge $var2</code></td>
<td>Test von nummerischen Werten auf &lt;, &gt;, &lt;=, &gt;=</td>
</tr>
<tr>
<td><code>-d FILE</code></td>
<td>FILE is a directory</td>
</tr>
<tr>
<td><code>-e FILE</code></td>
<td>FILE exists</td>
</tr>
<tr>
<td><code>-r, -s, -w, -x</code></td>
<td>FILE exists and readable, size is greater than zero, writeable, executable</td>
</tr>
</tbody>
</table><h3 id="verkettung">Verkettung</h3>
<p><code>command1 &amp;&amp; command2 &amp;&amp; ...</code> alle Kommandos ausführen, <strong>lazy evaluation</strong>, sobald ein Kommando nicht funktioniert wird abgebrochen<br>
für ODER Verkettung <code>||</code> benutzen<br>
für <strong>IF</strong>:</p>
<pre class=" language-bash"><code class="prism  language-bash"><span class="token keyword">if</span> <span class="token punctuation">[</span> <span class="token variable">$firstname</span><span class="token operator">=</span><span class="token string">"Daniel"</span> <span class="token punctuation">]</span> <span class="token operator">&amp;&amp;</span> <span class="token punctuation">[</span> <span class="token variable">$lastname</span><span class="token operator">=</span><span class="token string">"Datascientest"</span> <span class="token punctuation">]</span>
</code></pre>
<h3 id="while">WHILE</h3>
<pre class=" language-bash"><code class="prism  language-bash"><span class="token keyword">let</span> i<span class="token operator">=</span>0

<span class="token keyword">while</span> <span class="token punctuation">[</span> <span class="token variable">$i</span> -lt 10 <span class="token punctuation">]</span>
<span class="token keyword">do</span>
<span class="token keyword">let</span> <span class="token string">"i=i+1"</span>
<span class="token keyword">done</span>
<span class="token keyword">echo</span> <span class="token variable">$i</span>
</code></pre>
<h3 id="for">FOR</h3>
<pre class=" language-bash"><code class="prism  language-bash"><span class="token keyword">for</span> x <span class="token keyword">in</span> <span class="token string">'1st iteration'</span> <span class="token string">'2nd iteration'</span> <span class="token string">'3rd iteration'</span>
<span class="token keyword">do</span>
<span class="token keyword">echo</span> <span class="token variable">$x</span>
<span class="token keyword">done</span>
<span class="token comment"># Ausgabe: </span>
1st iteration
2nd iteration
3rd iteration
</code></pre>
<h4 id="alternative">Alternative</h4>
<p>Zur besseren Lesbarkeit werden arithmetische Ausdrücke in doppelte Klammern gepackt</p>
<pre class=" language-bash"><code class="prism  language-bash">arr <span class="token operator">=</span> <span class="token punctuation">(</span><span class="token string">'1st iteration'</span> <span class="token string">'2nd iteration'</span> <span class="token string">'3rd iteration'</span><span class="token punctuation">)</span>
<span class="token keyword">for</span> <span class="token variable"><span class="token punctuation">((</span>i<span class="token operator">=</span><span class="token number">0</span><span class="token punctuation">;</span> i<span class="token operator">&lt;</span>${#arr[@]}<span class="token punctuation">;</span> i<span class="token operator">++</span><span class="token punctuation">))</span></span> 
<span class="token keyword">do</span>
<span class="token keyword">echo</span> <span class="token variable">${arr[$i]}</span>
<span class="token keyword">done</span>
<span class="token comment"># Ausgabe: </span>
1st iteration
2nd iteration
3rd iteration
</code></pre>
<h3 id="case">CASE</h3>
<pre class=" language-bash"><code class="prism  language-bash"><span class="token keyword">for</span> x <span class="token keyword">in</span> <span class="token string">'1st iteration'</span> <span class="token string">'2nd iteration'</span> <span class="token string">'3rd iteration'</span>
<span class="token keyword">do</span>
    <span class="token keyword">case</span> <span class="token string">"<span class="token variable">$x</span>"</span> <span class="token keyword">in</span>
        <span class="token string">"1st iteration"</span><span class="token punctuation">)</span>
            <span class="token keyword">echo</span> <span class="token string">"Erste Iteration"</span>
            <span class="token punctuation">;</span><span class="token punctuation">;</span>
        <span class="token string">"2nd iteration"</span><span class="token punctuation">)</span>
            <span class="token keyword">echo</span> <span class="token string">"Zweite Iteration"</span>
            <span class="token punctuation">;</span><span class="token punctuation">;</span>
        <span class="token string">"3rd iteration"</span><span class="token punctuation">)</span>
            <span class="token keyword">echo</span> <span class="token string">"Dritte Iteration"</span>
            <span class="token punctuation">;</span><span class="token punctuation">;</span>
        *<span class="token punctuation">)</span>
            <span class="token keyword">echo</span> <span class="token string">"Unbekannte Iteration"</span>
            <span class="token punctuation">;</span><span class="token punctuation">;</span>
    esac
<span class="token keyword">done</span>
</code></pre>
<h3 id="arrays">Arrays</h3>
<pre class=" language-bash"><code class="prism  language-bash"><span class="token comment"># Array deklarieren </span>
colors<span class="token operator">=</span><span class="token punctuation">(</span><span class="token string">'rot'</span>  <span class="token string">'grün'</span>  <span class="token string">'blau'</span>  <span class="token string">'gelb'</span><span class="token punctuation">)</span> 

<span class="token comment"># Auf Elemente des Arrays zugreifen  </span>
<span class="token keyword">echo</span>  <span class="token string">"Das erste Element des Arrays: <span class="token variable">${colors[0]}</span>"</span>  
<span class="token keyword">echo</span>  <span class="token string">"Das zweite Element des Arrays: <span class="token variable">${colors[1]}</span>"</span>
<span class="token keyword">echo</span>  <span class="token string">"Alle Elemente des Arrays: <span class="token variable">${colors[@]}</span>"</span>
</code></pre>
<p>Länge des gesamten Arrays:</p>
<pre class=" language-bash"><code class="prism  language-bash"><span class="token keyword">echo</span> <span class="token variable">${#arr[@]}</span>
<span class="token comment"># Alternative</span>
<span class="token keyword">echo</span> <span class="token variable">${#arr[*]}</span>
</code></pre>
<p>Länge eines Elements:</p>
<pre class=" language-bash"><code class="prism  language-bash"><span class="token keyword">echo</span> <span class="token variable">${#arr[0]}</span>
</code></pre>
<h4 id="string-in-array-konvertieren">String in Array konvertieren</h4>
<pre class=" language-bash"><code class="prism  language-bash">my_string <span class="token operator">=</span> <span class="token string">"aa,bb,cc"</span>
<span class="token function">read</span> -ra my_arr <span class="token operator">&lt;&lt;&lt;</span> <span class="token punctuation">$(</span>echo <span class="token variable">$my_string</span> <span class="token operator">|</span> <span class="token function">tr</span> <span class="token string">','</span> <span class="token string">' '</span><span class="token punctuation">)</span>
</code></pre>
<p>read -r -&gt; Zeichen nicht interpretieren (zB bei )<br>
read -a -&gt; als array einlesen</p>
<h4 id="weitere-beispiele">Weitere Beispiele</h4>
<pre class=" language-bash"><code class="prism  language-bash">my_ar<span class="token operator">=</span><span class="token punctuation">(</span>hello world<span class="token punctuation">)</span>
<span class="token keyword">echo</span> <span class="token variable">${my_ar[0]}</span>
<span class="token comment"># Ausgabe: hello </span>
my_ar<span class="token punctuation">[</span>0<span class="token punctuation">]</span><span class="token operator">=</span>neu <span class="token comment"># Achtung: keine Leerzeichen</span>
<span class="token keyword">echo</span> <span class="token variable">${my_ar[*]}</span>
<span class="token comment"># Ausgabe: neu world</span>
my_ar<span class="token punctuation">[</span>666<span class="token punctuation">]</span><span class="token operator">=</span><span class="token string">"zwei wörter"</span>
<span class="token keyword">echo</span> <span class="token punctuation">(</span><span class="token operator">!</span>my_ar<span class="token punctuation">[</span>*<span class="token punctuation">]</span><span class="token punctuation">)</span>
<span class="token comment"># AUsgabe 0 1 666</span>
<span class="token keyword">echo</span> <span class="token variable">${#my_ar}</span>
<span class="token comment"># Ausgabe: 3</span>
<span class="token keyword">echo</span> <span class="token variable">${my_ar[*]}</span>
<span class="token comment"># Ausgabe: neu world zwei wörter</span>
<span class="token keyword">echo</span> <span class="token punctuation">{</span>1<span class="token punctuation">..</span>10<span class="token punctuation">}</span>
<span class="token comment"># Ausgabe: 1 2 3 4 5 6 7 8 9 10</span>
<span class="token comment"># Array erzeugen</span>
my_ar <span class="token operator">=</span><span class="token punctuation">(</span><span class="token punctuation">{</span>1<span class="token punctuation">..</span>10<span class="token punctuation">}</span><span class="token punctuation">)</span>
<span class="token comment"># die runden Klammern dürfen nicht fehlen !!!</span>
</code></pre>
<h4 id="sequenzen">Sequenzen</h4>
<p>Können gut in den Schleifenköpfen verwendet werden</p>
<pre class=" language-bash"><code class="prism  language-bash"><span class="token function">seq</span> 1 10
<span class="token comment"># Ausgabe:</span>
1
2
<span class="token comment"># ...</span>
10
<span class="token comment"># Kurzschreibweise</span>
<span class="token punctuation">{</span>1<span class="token punctuation">..</span>10<span class="token punctuation">}</span>
</code></pre>
<h3 id="functions">Functions</h3>
<pre class=" language-bash"><code class="prism  language-bash"><span class="token keyword">function</span> my_function<span class="token punctuation">(</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
<span class="token keyword">echo</span> <span class="token string">"First argument"</span>
<span class="token keyword">echo</span> <span class="token variable">$1</span>
<span class="token keyword">echo</span> <span class="token string">"Second argument"</span>
<span class="token keyword">echo</span> <span class="token variable">$2</span>
<span class="token punctuation">}</span>
<span class="token comment"># Aufruf:</span>
my_function <span class="token string">"Daniel"</span> <span class="token string">"24"</span>
</code></pre>
<h3 id="shift">shift</h3>
<p>Die <code>shift</code>-Anweisung in einem Shell-Skript verschiebt die Argumente, die an das Skript übergeben wurden. Normalerweise werden in Shell-Skripten die Argumente in den sogenannten “Positional Parameters” gespeichert, das heißt, das erste Argument wird in <code>$1</code>, das zweite in <code>$2</code> usw. gespeichert.</p>
<h3 id="here-konstrukte">HERE Konstrukte</h3>
<p>In der Shell gibt es verschiedene Arten von “Here-Dokumenten” oder “Here-Strings”, die verwendet werden können, um Eingaben an Befehle oder Skripte zu übergeben. Hier sind einige der gebräuchlichsten:</p>
<ol>
<li>
<p><strong>Here-Dokumente (<code>&lt;&lt;</code>):</strong> Ein Here-Dokument ermöglicht es dir, einen Block von Text als Eingabe an einen Befehl oder ein Skript zu übergeben. Der Block beginnt mit <code>&lt;&lt;</code> gefolgt von einem Token, das das Ende des Blocks kennzeichnet. Zum Beispiel:<br>
<code>cat &lt;&lt;END Das ist ein Here-Dokument. Es kann mehrere Zeilen enthalten. END</code><br>
<a href="https://phoenixnap.com/kb/bash-heredoc">Weitere Informationen</a></p>
</li>
<li>
<p><strong>Here-Strings (<code>&lt;&lt;&lt;</code>):</strong> Ein Here-String ermöglicht es dir, einen String als Eingabe an einen Befehl zu übergeben. Er ähnelt einem Here-Dokument, aber er ist einfacher und kann nur aus einer einzigen Zeile bestehen. Zum Beispiel:<br>
<code>echo "Das ist ein Here-String" &lt;&lt;&lt; "Hier ist der String."</code></p>
</li>
</ol>
<h3 id="beispiel-skript-websetup_static.sh">Beispiel Skript <code>websetup_static.sh</code></h3>
<pre class=" language-bash"><code class="prism  language-bash"><span class="token shebang important">#!/bin/bash</span>

PACKAGE<span class="token operator">=</span><span class="token string">"httpd wget unzip"</span>

SVC<span class="token operator">=</span><span class="token string">"httpd"</span>

URL<span class="token operator">=</span><span class="token string">"https://www.tooplate.com/zip-templates/2098_health.zip"</span>

ART_NAME<span class="token operator">=</span><span class="token string">"2098_health"</span>

TEMPDIR<span class="token operator">=</span><span class="token string">"/mtp/webfiles"</span>

<span class="token comment"># Installing Dependencies</span>

<span class="token keyword">echo</span> <span class="token string">"############################################################"</span>

<span class="token keyword">echo</span> <span class="token string">"Installing Dependencies"</span>

<span class="token keyword">echo</span> <span class="token string">"############################################################"</span>

<span class="token keyword">echo</span>

<span class="token function">sudo</span> yum <span class="token function">install</span> <span class="token variable">$PACKAGE</span> -y <span class="token operator">&gt;</span>/dev/null

  

<span class="token comment"># Start &amp; Enable Service</span>

<span class="token keyword">echo</span> <span class="token string">"############################################################"</span>

<span class="token keyword">echo</span> <span class="token string">"Start &amp; Enable HTTPD Service"</span>

<span class="token keyword">echo</span> <span class="token string">"############################################################"</span>

<span class="token keyword">echo</span>

<span class="token function">sudo</span> systemctl start <span class="token variable">$SVC</span>

<span class="token function">sudo</span> systemctl <span class="token function">enable</span> <span class="token variable">$SVC</span>

  

<span class="token comment"># Creating Temp Directory</span>

<span class="token keyword">echo</span> <span class="token string">"############################################################"</span>

<span class="token keyword">echo</span> <span class="token string">"Starting Artifact Deployment"</span>

<span class="token keyword">echo</span> <span class="token string">"############################################################"</span>

<span class="token keyword">echo</span>

<span class="token function">mkdir</span> -p <span class="token variable">$TEMPDIR</span>

<span class="token function">cd</span> <span class="token variable">$TEMPDIR</span>

  

<span class="token comment"># Downloading HTML Code</span>

<span class="token keyword">echo</span> <span class="token string">"############################################################"</span>

<span class="token keyword">echo</span> <span class="token string">"Downloading HTML Code"</span>

<span class="token keyword">echo</span> <span class="token string">"############################################################"</span>

<span class="token keyword">echo</span>

<span class="token function">wget</span> <span class="token variable">$URL</span>

unzip <span class="token variable">$ART_NAME</span>.zip

<span class="token function">sudo</span> <span class="token function">cp</span> -rf <span class="token variable">$ART_NAME</span>/* /var/www/html
</code></pre>

