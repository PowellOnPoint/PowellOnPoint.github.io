<!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xhtml" lang="en" xml:lang="en"><head>

<meta charset="utf-8">
<meta name="generator" content="quarto-1.8.27">

<meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=yes">

<meta name="description" content="Experimenting with R guided by test questions">

<title>Central Limit Theorem and Data Visualization study</title>
<style>
code{white-space: pre-wrap;}
span.smallcaps{font-variant: small-caps;}
div.columns{display: flex; gap: min(4vw, 1.5em);}
div.column{flex: auto; overflow-x: auto;}
div.hanging-indent{margin-left: 1.5em; text-indent: -1.5em;}
ul.task-list{list-style: none;}
ul.task-list li input[type="checkbox"] {
  width: 0.8em;
  margin: 0 0.8em 0.2em -1em; /* quarto-specific, see https://github.com/quarto-dev/quarto-cli/issues/4556 */ 
  vertical-align: middle;
}
/* CSS for syntax highlighting */
html { -webkit-text-size-adjust: 100%; }
pre > code.sourceCode { white-space: pre; position: relative; }
pre > code.sourceCode > span { display: inline-block; line-height: 1.25; }
pre > code.sourceCode > span:empty { height: 1.2em; }
.sourceCode { overflow: visible; }
code.sourceCode > span { color: inherit; text-decoration: inherit; }
div.sourceCode { margin: 1em 0; }
pre.sourceCode { margin: 0; }
@media screen {
div.sourceCode { overflow: auto; }
}
@media print {
pre > code.sourceCode { white-space: pre-wrap; }
pre > code.sourceCode > span { text-indent: -5em; padding-left: 5em; }
}
pre.numberSource code
  { counter-reset: source-line 0; }
pre.numberSource code > span
  { position: relative; left: -4em; counter-increment: source-line; }
pre.numberSource code > span > a:first-child::before
  { content: counter(source-line);
    position: relative; left: -1em; text-align: right; vertical-align: baseline;
    border: none; display: inline-block;
    -webkit-touch-callout: none; -webkit-user-select: none;
    -khtml-user-select: none; -moz-user-select: none;
    -ms-user-select: none; user-select: none;
    padding: 0 4px; width: 4em;
  }
pre.numberSource { margin-left: 3em;  padding-left: 4px; }
div.sourceCode
  {   }
@media screen {
pre > code.sourceCode > span > a:first-child::before { text-decoration: underline; }
}
</style>


<script src="Aaron_Powell_ForLiveSession_Unit2_files/libs/clipboard/clipboard.min.js"></script>
<script src="Aaron_Powell_ForLiveSession_Unit2_files/libs/quarto-html/quarto.js" type="module"></script>
<script src="Aaron_Powell_ForLiveSession_Unit2_files/libs/quarto-html/tabsets/tabsets.js" type="module"></script>
<script src="Aaron_Powell_ForLiveSession_Unit2_files/libs/quarto-html/axe/axe-check.js" type="module"></script>
<script src="Aaron_Powell_ForLiveSession_Unit2_files/libs/quarto-html/popper.min.js"></script>
<script src="Aaron_Powell_ForLiveSession_Unit2_files/libs/quarto-html/tippy.umd.min.js"></script>
<script src="Aaron_Powell_ForLiveSession_Unit2_files/libs/quarto-html/anchor.min.js"></script>
<link href="Aaron_Powell_ForLiveSession_Unit2_files/libs/quarto-html/tippy.css" rel="stylesheet">
<link href="Aaron_Powell_ForLiveSession_Unit2_files/libs/quarto-html/quarto-syntax-highlighting-ed96de9b727972fe78a7b5d16c58bf87.css" rel="stylesheet" id="quarto-text-highlighting-styles">
<script src="Aaron_Powell_ForLiveSession_Unit2_files/libs/bootstrap/bootstrap.min.js"></script>
<link href="Aaron_Powell_ForLiveSession_Unit2_files/libs/bootstrap/bootstrap-icons.css" rel="stylesheet">
<link href="Aaron_Powell_ForLiveSession_Unit2_files/libs/bootstrap/bootstrap-d6a003b94517c951b2d65075d42fb01b.min.css" rel="stylesheet" append-hash="true" id="quarto-bootstrap" data-mode="light">
<link href="Aaron_Powell_ForLiveSession_Unit2_files/libs/htmltools-fill-0.5.9/fill.css" rel="stylesheet">
<script src="Aaron_Powell_ForLiveSession_Unit2_files/libs/htmlwidgets-1.6.4/htmlwidgets.js"></script>
<script src="Aaron_Powell_ForLiveSession_Unit2_files/libs/plotly-binding-4.11.0/plotly.js"></script>
<script src="Aaron_Powell_ForLiveSession_Unit2_files/libs/typedarray-0.1/typedarray.min.js"></script>
<script src="Aaron_Powell_ForLiveSession_Unit2_files/libs/jquery-3.5.1/jquery.min.js"></script>
<link href="Aaron_Powell_ForLiveSession_Unit2_files/libs/crosstalk-1.2.2/css/crosstalk.min.css" rel="stylesheet">
<script src="Aaron_Powell_ForLiveSession_Unit2_files/libs/crosstalk-1.2.2/js/crosstalk.min.js"></script>
<link href="Aaron_Powell_ForLiveSession_Unit2_files/libs/plotly-htmlwidgets-css-2.11.1/plotly-htmlwidgets.css" rel="stylesheet">
<script src="Aaron_Powell_ForLiveSession_Unit2_files/libs/plotly-main-2.11.1/plotly-latest.min.js"></script>


</head>

<body class="fullcontent quarto-light">

<div id="quarto-content" class="page-columns page-rows-contents page-layout-article">

<main class="content" id="quarto-document-content">

<header id="title-block-header" class="quarto-title-block default">
<div class="quarto-title">
<h1 class="title">Central Limit Theorem and Data Visualization study</h1>
</div>

<div>
  <div class="description">
    Experimenting with R guided by test questions
  </div>
</div>


<div class="quarto-title-meta">

    
  
    
  </div>
  


</header>


<section id="data-visualization-with-playerbball.csv" class="level2">
<h2 class="anchored" data-anchor-id="data-visualization-with-playerbball.csv">Data Visualization with PlayerBBall.csv</h2>
<div class="cell">
<div class="code-copy-outer-scaffold"><div class="sourceCode cell-code" id="cb1"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb1-1"><a href="#cb1-1" aria-hidden="true" tabindex="-1"></a>player_data <span class="ot">&lt;-</span> <span class="fu">read.csv</span>(<span class="st">"PlayersBBall.csv"</span>)</span>
<span id="cb1-2"><a href="#cb1-2" aria-hidden="true" tabindex="-1"></a><span class="fu">glimpse</span>(player_data)</span></code></pre></div><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></div>
<div class="cell-output cell-output-stdout">
<pre><code>Rows: 4,550
Columns: 8
$ name       &lt;chr&gt; "Alaa Abdelnaby", "Zaid Abdul-Aziz", "Kareem Abdul-Jabbar",…
$ year_start &lt;int&gt; 1991, 1969, 1970, 1991, 1998, 1997, 1977, 1957, 1947, 2017,…
$ year_end   &lt;int&gt; 1995, 1978, 1989, 2001, 2003, 2008, 1981, 1957, 1948, 2018,…
$ position   &lt;chr&gt; "F-C", "C-F", "C", "G", "F", "F", "F", "G", "F", "G-F", "G"…
$ height     &lt;chr&gt; "6-10", "6-9", "7-2", "6-1", "6-6", "6-9", "6-7", "6-3", "6…
$ weight     &lt;int&gt; 240, 235, 225, 162, 223, 225, 220, 180, 195, 190, 185, 183,…
$ birth_date &lt;chr&gt; "June 24, 1968", "April 7, 1946", "April 16, 1947", "March …
$ college    &lt;chr&gt; "Duke University", "Iowa State University", "University of …</code></pre>
</div>
</div>
<section id="use-the-playerbball.csv-dataset-to-visually-represent-summarize-the-number-of-players-in-each-position." class="level4">
<h4 class="anchored" data-anchor-id="use-the-playerbball.csv-dataset-to-visually-represent-summarize-the-number-of-players-in-each-position.">Use the PlayerBBall.csv dataset to visually represent (summarize) the number of players in each position.</h4>
<div class="cell">
<div class="code-copy-outer-scaffold"><div class="sourceCode cell-code" id="cb3"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb3-1"><a href="#cb3-1" aria-hidden="true" tabindex="-1"></a><span class="fu">ggplot</span>(player_data, <span class="fu">aes</span>(<span class="at">x =</span> position)) <span class="sc">+</span> <span class="co"># May fct_recode(position, "C" = "Center"...)</span></span>
<span id="cb3-2"><a href="#cb3-2" aria-hidden="true" tabindex="-1"></a>  <span class="fu">geom_bar</span>(<span class="at">fill =</span> <span class="st">"skyblue"</span>) <span class="sc">+</span></span>
<span id="cb3-3"><a href="#cb3-3" aria-hidden="true" tabindex="-1"></a>  <span class="fu">labs</span>(<span class="at">title =</span> <span class="st">"Number of Players by Position"</span>, <span class="at">x =</span> <span class="st">"Position"</span>, <span class="at">y =</span> <span class="st">"Count"</span>) <span class="sc">+</span></span>
<span id="cb3-4"><a href="#cb3-4" aria-hidden="true" tabindex="-1"></a>  <span class="fu">theme_bw</span>()</span></code></pre></div><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></div>
<div class="cell-output-display">
<div>
<figure class="figure">
<p><img src="Aaron_Powell_ForLiveSession_Unit2_files/figure-html/players%20by%20position-1.png" class="img-fluid figure-img" width="672"></p>
</figure>
</div>
</div>
</div>
<p>This baysian theme chart reveals a possible empty cell. Viewing the Data Table reveals one observation with an empty value. Let’s create a copy of the data table without empty cells for further analysis and fix the bar chart.</p>
<div class="cell">
<div class="code-copy-outer-scaffold"><div class="sourceCode cell-code" id="cb4"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb4-1"><a href="#cb4-1" aria-hidden="true" tabindex="-1"></a>player_data <span class="ot">&lt;-</span> player_data <span class="sc">%&gt;%</span> <span class="fu">filter</span>(position <span class="sc">!=</span> <span class="st">""</span>)</span>
<span id="cb4-2"><a href="#cb4-2" aria-hidden="true" tabindex="-1"></a><span class="fu">ggplot</span>(player_data, <span class="fu">aes</span>(<span class="at">x =</span> position)) <span class="sc">+</span> <span class="co"># May fct_recode(position, "C" = "Center"...)</span></span>
<span id="cb4-3"><a href="#cb4-3" aria-hidden="true" tabindex="-1"></a>  <span class="fu">geom_bar</span>(<span class="at">fill =</span> <span class="st">"skyblue"</span>) <span class="sc">+</span></span>
<span id="cb4-4"><a href="#cb4-4" aria-hidden="true" tabindex="-1"></a>  <span class="fu">labs</span>(<span class="at">title =</span> <span class="st">"Number of Players by Position"</span>, <span class="at">x =</span> <span class="st">"Position"</span>, <span class="at">y =</span> <span class="st">"Count"</span>) <span class="sc">+</span></span>
<span id="cb4-5"><a href="#cb4-5" aria-hidden="true" tabindex="-1"></a>  <span class="fu">theme_bw</span>()</span></code></pre></div><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></div>
<div class="cell-output-display">
<div>
<figure class="figure">
<p><img src="Aaron_Powell_ForLiveSession_Unit2_files/figure-html/filter%20empty%20position-1.png" class="img-fluid figure-img" width="672"></p>
</figure>
</div>
</div>
</div>
</section>
<section id="use-the-dataset-to-visually-investigate-the-distribution-of-the-weight-of-centers-c-is-greater-than-the-distribution-of-the-weight-of-forwards-f." class="level4">
<h4 class="anchored" data-anchor-id="use-the-dataset-to-visually-investigate-the-distribution-of-the-weight-of-centers-c-is-greater-than-the-distribution-of-the-weight-of-forwards-f.">Use the dataset to visually investigate the distribution of the weight of centers (C) is greater than the distribution of the weight of forwards (F).</h4>
<div class="cell">
<div class="code-copy-outer-scaffold"><div class="sourceCode cell-code" id="cb5"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb5-1"><a href="#cb5-1" aria-hidden="true" tabindex="-1"></a><span class="fu">ggplot</span>(player_data <span class="sc">%&gt;%</span> <span class="fu">filter</span>(position <span class="sc">%in%</span> <span class="fu">c</span>(<span class="st">"C"</span>, <span class="st">"F"</span>)), <span class="fu">aes</span>(<span class="at">x =</span> weight, <span class="at">fill =</span> position)) <span class="sc">+</span></span>
<span id="cb5-2"><a href="#cb5-2" aria-hidden="true" tabindex="-1"></a>  <span class="fu">geom_density</span>(<span class="at">alpha =</span> <span class="fl">0.5</span>) <span class="sc">+</span> <span class="co"># alpha to help with overlapping areas</span></span>
<span id="cb5-3"><a href="#cb5-3" aria-hidden="true" tabindex="-1"></a>  <span class="fu">labs</span>(<span class="at">title =</span> <span class="st">"Weight Distribution: Centers vs Forwards"</span>, <span class="at">x =</span> <span class="st">"Weight"</span>, <span class="at">y =</span> <span class="st">"Density"</span>) <span class="sc">+</span></span>
<span id="cb5-4"><a href="#cb5-4" aria-hidden="true" tabindex="-1"></a>  <span class="fu">theme_bw</span>()</span></code></pre></div><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></div>
<div class="cell-output cell-output-stderr">
<pre><code>Warning: Removed 3 rows containing non-finite outside the scale range
(`stat_density()`).</code></pre>
</div>
<div class="cell-output-display">
<div>
<figure class="figure">
<p><img src="Aaron_Powell_ForLiveSession_Unit2_files/figure-html/weight%20distribution%20centers%20vs%20forwards-1.png" class="img-fluid figure-img" width="672"></p>
</figure>
</div>
</div>
</div>
<p>For the scope of this exercise, we’ll disregard the warnings about null values. The density plot suggests that centers (C) generally have a higher weight distribution compared to forwards (F), as the density curve for centers is shifted to the right of the curve for forwards. This indicates that centers tend to be heavier than forwards on average.</p>
</section>
<section id="use-the-dataset-to-visually-investigate-if-the-distribution-of-the-height-of-centers-c-is-greater-than-the-distribution-of-the-height-of-forwards-f." class="level4">
<h4 class="anchored" data-anchor-id="use-the-dataset-to-visually-investigate-if-the-distribution-of-the-height-of-centers-c-is-greater-than-the-distribution-of-the-height-of-forwards-f.">Use the dataset to visually investigate if the distribution of the height of centers (C) is greater than the distribution of the height of forwards (F).</h4>
<div class="cell">
<div class="code-copy-outer-scaffold"><div class="sourceCode cell-code" id="cb7"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb7-1"><a href="#cb7-1" aria-hidden="true" tabindex="-1"></a><span class="fu">ggplot</span>(player_data <span class="sc">%&gt;%</span> <span class="fu">filter</span>(position <span class="sc">%in%</span> <span class="fu">c</span>(<span class="st">"C"</span>, <span class="st">"F"</span>)), <span class="fu">aes</span>(<span class="at">x =</span> height, <span class="at">fill =</span> position)) <span class="sc">+</span> <span class="co"># str data probably not going to look good. </span></span>
<span id="cb7-2"><a href="#cb7-2" aria-hidden="true" tabindex="-1"></a>  <span class="fu">geom_density</span>(<span class="at">alpha =</span> <span class="fl">0.5</span>) <span class="sc">+</span></span>
<span id="cb7-3"><a href="#cb7-3" aria-hidden="true" tabindex="-1"></a>  <span class="fu">labs</span>(<span class="at">title =</span> <span class="st">"Weight Distribution: Centers vs Forwards"</span>, <span class="at">x =</span> <span class="st">'Height'</span>, <span class="at">y =</span> <span class="st">"Density"</span>) <span class="sc">+</span></span>
<span id="cb7-4"><a href="#cb7-4" aria-hidden="true" tabindex="-1"></a>  <span class="fu">theme_bw</span>()</span></code></pre></div><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></div>
<div class="cell-output cell-output-stderr">
<pre><code>Warning: Groups with fewer than two data points have been dropped.
Groups with fewer than two data points have been dropped.</code></pre>
</div>
<div class="cell-output cell-output-stderr">
<pre><code>Warning: Removed 2 rows containing missing values or values outside the scale range
(`geom_density()`).</code></pre>
</div>
<div class="cell-output-display">
<div>
<figure class="figure">
<p><img src="Aaron_Powell_ForLiveSession_Unit2_files/figure-html/height%20distribution%20centers%20vs%20forwards-1.png" class="img-fluid figure-img" width="672"></p>
</figure>
</div>
</div>
</div>
<p>Not a great visual, not to mention several warning messages. This is due to the height data being stored as strings. Let’s convert the height data to an integer.</p>
<div class="cell">
<div class="code-copy-outer-scaffold"><div class="sourceCode cell-code" id="cb10"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb10-1"><a href="#cb10-1" aria-hidden="true" tabindex="-1"></a>player_data <span class="ot">&lt;-</span> player_data <span class="sc">%&gt;%</span></span>
<span id="cb10-2"><a href="#cb10-2" aria-hidden="true" tabindex="-1"></a>  <span class="fu">mutate</span>(<span class="at">height_inches =</span> <span class="fu">as.numeric</span>(<span class="fu">str_split_fixed</span>(height, <span class="st">"-"</span>, <span class="dv">2</span>)[,<span class="dv">1</span>]) <span class="sc">*</span> <span class="dv">12</span> <span class="sc">+</span> <span class="co"># Copilot is suggestion numeric...  </span></span>
<span id="cb10-3"><a href="#cb10-3" aria-hidden="true" tabindex="-1"></a>                        <span class="fu">as.numeric</span>(<span class="fu">str_split_fixed</span>(height, <span class="st">"-"</span>, <span class="dv">2</span>)[,<span class="dv">2</span>]))</span></code></pre></div><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></div>
</div>
<p>Discovered the numeric datatype in R is the default for decimal numbers and is also referred to as “double”. This appears to be equivelant to the floating point datatype in Python.</p>
<p>Now let’s re-create the height distribution plot for centers vs forwards.</p>
<div class="cell">
<div class="code-copy-outer-scaffold"><div class="sourceCode cell-code" id="cb11"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb11-1"><a href="#cb11-1" aria-hidden="true" tabindex="-1"></a><span class="fu">ggplot</span>(player_data <span class="sc">%&gt;%</span> <span class="fu">filter</span>(position <span class="sc">%in%</span> <span class="fu">c</span>(<span class="st">"C"</span>, <span class="st">"F"</span>)), <span class="fu">aes</span>(<span class="at">x =</span> height_inches, <span class="at">fill =</span> position)) <span class="sc">+</span></span>
<span id="cb11-2"><a href="#cb11-2" aria-hidden="true" tabindex="-1"></a>  <span class="fu">geom_density</span>(<span class="at">alpha =</span> <span class="fl">0.5</span>) <span class="sc">+</span></span>
<span id="cb11-3"><a href="#cb11-3" aria-hidden="true" tabindex="-1"></a>  <span class="fu">labs</span>(<span class="at">title =</span> <span class="st">"Height Distribution: Centers vs Forwards"</span>, <span class="at">x =</span> <span class="st">'Height (inches)'</span>, <span class="at">y =</span> <span class="st">"Density"</span>) <span class="sc">+</span></span>
<span id="cb11-4"><a href="#cb11-4" aria-hidden="true" tabindex="-1"></a>  <span class="fu">theme_bw</span>()</span></code></pre></div><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></div>
<div class="cell-output-display">
<div>
<figure class="figure">
<p><img src="Aaron_Powell_ForLiveSession_Unit2_files/figure-html/height%20distribution%20centers%20vs%20forwards%20numeric-1.png" class="img-fluid figure-img" width="672"></p>
</figure>
</div>
</div>
</div>
</section>
<section id="use-the-dataset-to-visually-investigate-if-the-distribution-of-height-is-different-between-any-of-the-positions." class="level4">
<h4 class="anchored" data-anchor-id="use-the-dataset-to-visually-investigate-if-the-distribution-of-height-is-different-between-any-of-the-positions.">Use the dataset to visually investigate if the distribution of height is different between any of the positions.</h4>
<div class="cell">
<div class="code-copy-outer-scaffold"><div class="sourceCode cell-code" id="cb12"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb12-1"><a href="#cb12-1" aria-hidden="true" tabindex="-1"></a><span class="fu">ggplot</span>(player_data, <span class="fu">aes</span>(<span class="at">x =</span> height_inches, <span class="at">fill =</span> position)) <span class="sc">+</span></span>
<span id="cb12-2"><a href="#cb12-2" aria-hidden="true" tabindex="-1"></a>  <span class="fu">geom_density</span>(<span class="at">alpha =</span> <span class="fl">0.5</span>) <span class="sc">+</span></span>
<span id="cb12-3"><a href="#cb12-3" aria-hidden="true" tabindex="-1"></a>  <span class="fu">labs</span>(<span class="at">title =</span> <span class="st">"Height Distribution by Position"</span>, <span class="at">x =</span> <span class="st">'Height (inches)'</span>, <span class="at">y =</span> <span class="st">"Density"</span>) <span class="sc">+</span></span>
<span id="cb12-4"><a href="#cb12-4" aria-hidden="true" tabindex="-1"></a>  <span class="fu">theme_bw</span>()</span></code></pre></div><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></div>
<div class="cell-output-display">
<div>
<figure class="figure">
<p><img src="Aaron_Powell_ForLiveSession_Unit2_files/figure-html/height%20distribution%20by%20position-1.png" class="img-fluid figure-img" width="672"></p>
</figure>
</div>
</div>
</div>
</section>
<section id="use-the-dataset-to-investigate-how-the-players-height-is-related-to-the-players-weight.-how-does-height-change-as-the-weight-changes" class="level4">
<h4 class="anchored" data-anchor-id="use-the-dataset-to-investigate-how-the-players-height-is-related-to-the-players-weight.-how-does-height-change-as-the-weight-changes">Use the dataset to investigate how the player’s height is related to the player’s weight. How does height change as the weight changes?</h4>
<div class="cell">
<div class="code-copy-outer-scaffold"><div class="sourceCode cell-code" id="cb13"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb13-1"><a href="#cb13-1" aria-hidden="true" tabindex="-1"></a><span class="fu">ggplot</span>(player_data, <span class="fu">aes</span>(<span class="at">x =</span> weight, <span class="at">y =</span> height_inches, <span class="at">color =</span> position)) <span class="sc">+</span></span>
<span id="cb13-2"><a href="#cb13-2" aria-hidden="true" tabindex="-1"></a>  <span class="fu">geom_smooth</span>(<span class="at">alpha =</span> .<span class="dv">5</span>) <span class="sc">+</span> <span class="co"># alpha to help show overlap and clustering</span></span>
<span id="cb13-3"><a href="#cb13-3" aria-hidden="true" tabindex="-1"></a>  <span class="fu">labs</span>(<span class="at">title =</span> <span class="st">"Height vs Weight"</span>, <span class="at">x =</span> <span class="st">"Weight"</span>, <span class="at">y =</span> <span class="st">"Height (inches)"</span>) <span class="sc">+</span></span>
<span id="cb13-4"><a href="#cb13-4" aria-hidden="true" tabindex="-1"></a>  <span class="fu">theme_bw</span>()  <span class="co"># Would add a correlation factor here, but may be out of scope for this lesson.</span></span></code></pre></div><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></div>
<div class="cell-output cell-output-stderr">
<pre><code>`geom_smooth()` using method = 'gam' and formula = 'y ~ s(x, bs = "cs")'</code></pre>
</div>
<div class="cell-output cell-output-stderr">
<pre><code>Warning: Removed 5 rows containing non-finite outside the scale range
(`stat_smooth()`).</code></pre>
</div>
<div class="cell-output-display">
<div>
<figure class="figure">
<p><img src="Aaron_Powell_ForLiveSession_Unit2_files/figure-html/height%20vs%20weight-1.png" class="img-fluid figure-img" width="672"></p>
</figure>
</div>
</div>
</div>
</section>
<section id="is-their-any-difference-in-the-relationship-between-height-and-weight-between-positions-are-height-and-weight-related-differently-for-different-positions." class="level4">
<h4 class="anchored" data-anchor-id="is-their-any-difference-in-the-relationship-between-height-and-weight-between-positions-are-height-and-weight-related-differently-for-different-positions.">Is their any difference in the relationship between height and weight between positions? Are height and weight related differently for different positions.</h4>
<p>There is a positive correlation between height and weight for all positions, but the strength of this correlation varies. Centers (C) tend to be taller and heavier, while guards (G) are generally shorter and lighter. Forwards (F) fall in between these two extremes. This suggests that different positions have different physical requirements, which is reflected in the height-weight relationship.</p>
</section>
<section id="a-historian-would-like-to-investigate-the-claim-that-the-heights-of-players-have-increased-over-the-years.-analyze-this-claim-graphically-visually.-create-a-3d-plot-of-height-vs.-weight-vs.-year-and-color-code-the-points-by-position." class="level4">
<h4 class="anchored" data-anchor-id="a-historian-would-like-to-investigate-the-claim-that-the-heights-of-players-have-increased-over-the-years.-analyze-this-claim-graphically-visually.-create-a-3d-plot-of-height-vs.-weight-vs.-year-and-color-code-the-points-by-position.">A historian would like to investigate the claim that the heights of players have increased over the years. Analyze this claim graphically / visually. Create a 3D plot of height vs.&nbsp;weight vs.&nbsp;year and color code the points by position.</h4>
<p>Prepping the data for a cleaner visual. Interpolate the year as the midpoint between year_start and year_end. Use a ratio of height to weight to remove clutter of two variables.</p>
<div class="cell">
<div class="code-copy-outer-scaffold"><div class="sourceCode cell-code" id="cb16"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb16-1"><a href="#cb16-1" aria-hidden="true" tabindex="-1"></a>player_data <span class="ot">&lt;-</span> player_data <span class="sc">%&gt;%</span></span>
<span id="cb16-2"><a href="#cb16-2" aria-hidden="true" tabindex="-1"></a>  <span class="fu">mutate</span>(<span class="at">year_mid =</span> (year_start <span class="sc">+</span> year_end) <span class="sc">/</span> <span class="dv">2</span>)</span>
<span id="cb16-3"><a href="#cb16-3" aria-hidden="true" tabindex="-1"></a>player_data <span class="ot">&lt;-</span> player_data <span class="sc">%&gt;%</span></span>
<span id="cb16-4"><a href="#cb16-4" aria-hidden="true" tabindex="-1"></a>  <span class="fu">mutate</span>(<span class="at">hw_ratio =</span> (height_inches <span class="sc">/</span> weight))</span></code></pre></div><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></div>
</div>
<div class="cell">
<div class="code-copy-outer-scaffold"><div class="sourceCode cell-code" id="cb17"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb17-1"><a href="#cb17-1" aria-hidden="true" tabindex="-1"></a><span class="fu">ggplot</span>(player_data, <span class="fu">aes</span>(<span class="at">x =</span>year_mid, <span class="at">y =</span> height_inches)) <span class="sc">+</span></span>
<span id="cb17-2"><a href="#cb17-2" aria-hidden="true" tabindex="-1"></a>  <span class="fu">geom_smooth</span>(<span class="at">alpha =</span> .<span class="dv">5</span>) <span class="sc">+</span></span>
<span id="cb17-3"><a href="#cb17-3" aria-hidden="true" tabindex="-1"></a>  <span class="fu">labs</span>(<span class="at">title =</span> <span class="st">"Height vs Year"</span>, <span class="at">x =</span> <span class="st">"Mid Career (Year)"</span>, <span class="at">y =</span> <span class="st">"Height"</span>) <span class="sc">+</span></span>
<span id="cb17-4"><a href="#cb17-4" aria-hidden="true" tabindex="-1"></a>  <span class="fu">theme_bw</span>()</span></code></pre></div><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></div>
<div class="cell-output cell-output-stderr">
<pre><code>`geom_smooth()` using method = 'gam' and formula = 'y ~ s(x, bs = "cs")'</code></pre>
</div>
<div class="cell-output-display">
<div>
<figure class="figure">
<p><img src="Aaron_Powell_ForLiveSession_Unit2_files/figure-html/height%20vs%20year-1.png" class="img-fluid figure-img" width="672"></p>
</figure>
</div>
</div>
</div>
<p>There is enough of a trend to support the historian’s claim that player heights have increased over the years.</p>
<div class="cell">
<div class="code-copy-outer-scaffold"><div class="sourceCode cell-code" id="cb19"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb19-1"><a href="#cb19-1" aria-hidden="true" tabindex="-1"></a><span class="fu">library</span>(plotly)</span></code></pre></div><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></div>
<div class="cell-output cell-output-stderr">
<pre><code>
Attaching package: 'plotly'</code></pre>
</div>
<div class="cell-output cell-output-stderr">
<pre><code>The following object is masked from 'package:ggplot2':

    last_plot</code></pre>
</div>
<div class="cell-output cell-output-stderr">
<pre><code>The following object is masked from 'package:stats':

    filter</code></pre>
</div>
<div class="cell-output cell-output-stderr">
<pre><code>The following object is masked from 'package:graphics':

    layout</code></pre>
</div>
<div class="code-copy-outer-scaffold"><div class="sourceCode cell-code" id="cb24"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb24-1"><a href="#cb24-1" aria-hidden="true" tabindex="-1"></a>fig <span class="ot">&lt;-</span> <span class="fu">plot_ly</span>(player_data, <span class="at">x =</span> <span class="sc">~</span>weight, <span class="at">y =</span> <span class="sc">~</span>height_inches, <span class="at">z =</span> <span class="sc">~</span>year_end, <span class="at">color =</span> <span class="sc">~</span>position) <span class="sc">%&gt;%</span></span>
<span id="cb24-2"><a href="#cb24-2" aria-hidden="true" tabindex="-1"></a>  <span class="fu">add_markers</span>() <span class="sc">%&gt;%</span></span>
<span id="cb24-3"><a href="#cb24-3" aria-hidden="true" tabindex="-1"></a>  <span class="fu">layout</span>(<span class="at">title =</span> <span class="st">"Height vs Weight vs Year"</span>,</span>
<span id="cb24-4"><a href="#cb24-4" aria-hidden="true" tabindex="-1"></a>         <span class="at">scene =</span> <span class="fu">list</span>(<span class="at">xaxis =</span> <span class="fu">list</span>(<span class="at">title =</span> <span class="st">'Weight'</span>),</span>
<span id="cb24-5"><a href="#cb24-5" aria-hidden="true" tabindex="-1"></a>                      <span class="at">yaxis =</span> <span class="fu">list</span>(<span class="at">title =</span> <span class="st">'Height (inches)'</span>),</span>
<span id="cb24-6"><a href="#cb24-6" aria-hidden="true" tabindex="-1"></a>                      <span class="at">zaxis =</span> <span class="fu">list</span>(<span class="at">title =</span> <span class="st">'Year'</span>)))</span>
<span id="cb24-7"><a href="#cb24-7" aria-hidden="true" tabindex="-1"></a></span>
<span id="cb24-8"><a href="#cb24-8" aria-hidden="true" tabindex="-1"></a>fig</span></code></pre></div><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></div>
<div class="cell-output cell-output-stderr">
<pre><code>Warning: Ignoring 5 observations</code></pre>
</div>
<div class="cell-output-display">
<div class="plotly html-widget html-fill-item" id="htmlwidget-c93c6cbebf18c9ac8eae" style="width:100%;height:464px;"></div>
<script type="application/json" data-for="htmlwidget-c93c6cbebf18c9ac8eae">{"x":{"visdat":{"172046b7dfe1d":["function () ","plotlyVisDat"]},"cur_data":"172046b7dfe1d","attrs":{"172046b7dfe1d":{"x":{},"y":{},"z":{},"color":{},"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatter3d","mode":"markers","inherit":true}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"title":"Height vs Weight vs Year","scene":{"xaxis":{"title":"Weight"},"yaxis":{"title":"Height (inches)"},"zaxis":{"title":"Year"}},"hovermode":"closest","showlegend":true},"source":"A","config":{"modeBarButtonsToAdd":["hoverclosest","hovercompare"],"showSendToCloud":false},"data":[{"x":[225,255,248,251,225,250,260,250,260,245,230,240,249,245,280,255,255,235,250,255,210,205,250,230,290,240,260,200,225,225,210,225,250,240,235,210,360,240,240,252,220,230,265,260,200,230,230,240,257,215,230,225,235,227,230,252,235,244,225,225,235,248,245,250,240,225,240,285,240,215,240,235,245,255,240,230,275,240,255,265,212,235,253,260,255,275,210,250,245,235,200,280,215,245,250,275,295,260,242,255,265,220,217,265,245,270,220,234,251,245,220,240,240,241,215,300,243,262,275,210,225,250,270,250,279,275,235,220,215,275,220,240,275,230,235,260,245,240,255,255,260,255,235,220,240,288,240,240,235,265,235,230,250,225,255,240,255,220,225,255,243,205,235,240,220,280,250,245,250,245,270,230,218,260,255,254,240,225,235,245,260,330,262,260,240,225,249,225,275,280,205,268,190,215,240,270,248,220,230,240,240,205,230,245,265,245,220,220,238,230,245,220,270,240,300,237,210,255,205,245,245,240,210,210,265,210,265,253,228,315,245,265,245,260,260,245,230,260,245,250,255,235,215,215,225,245,220,265,220,260,240,251,235,245,275,230,245,285,250,325,228,240,220,260,250,220,285,245,265,275,255,280,259,250,220,253,290,225,250,220,208,270,240,245,232,270,225,240,245,255,210,257,265,245,210,244,280,310,235,221,270,225,260,230,235,266,247,240,275,275,250,303,245,235,255,198,240,235,230,260,248,217,240,220,245,230,241,210,225,230,220,280,255,260,325,250,245,250,240,255,255,215,269,255,280,240,240,220,270,240,230,220,225,240,232,230,307,270,240,270,240,210,220,247,240,308,256,250,260,248,265,280,220,255,220,250,250,275,250,230,230,235,257,275,255,250,230,245,210,285,235,235,250,255,215,200,215,279,270,240,231,230,245,256,240,255,212,260,225,230,250,230,305,235,235,260,230,305,245,248,210,250,250,250,235,235,240,220,250,250,225,270,265,225,220,235,236,230,260,245,264,235,255,235,220,235,245,230,245,260,260,265,263,215,230,260,215,240,285,240,260,265,255,260,220,218,245,275,260,220,260,225,220,225,258,225,225,245,245,250,250,220,260,265,210,225,275,231,235,225,270,235,220,245,230,255,250,240,240,265],"y":[86,84,86,85,81,83,83,83,82,83,82,86,84,81,83,84,82,82,82,85,84,82,84,84,83,82,82,81,81,84,79,83,84,83,82,80,89,83,79,85,82,84,84,84,91,82,83,84,84,82,82,82,90,82,87,86,84,84,83,83,82,82,84,81,84,86,83,84,82,83,82,83,85,83,84,85,85,85,82,84,87,82,84,84,84,82,77,83,83,84,82,83,82,82,83,82,84,85,84,83,83,81,79,84,84,83,79,80,83,84,78,82,82,83,83,84,85,83,86,78,80,85,83,86,83,84,83,84,83,88,81,83,84,80,84,82,83,84,83,83,83,81,83,83,85,85,85,84,83,84,82,80,82,81,83,83,82,82,82,85,84,76,84,86,83,85,83,85,82,84,84,81,79,86,82,86,82,81,87,84,84,86,84,84,82,82,84,81,82,84,84,84,81,81,83,86,84,79,84,81,84,78,81,85,83,85,83,84,87,85,84,82,82,82,84,84,83,84,80,83,83,78,79,80,83,84,83,84,81,86,83,84,83,85,83,83,82,86,84,83,83,84,79,78,80,84,80,84,81,84,84,85,82,83,83,82,83,82,83,88,84,83,82,85,85,82,83,81,86,84,84,84,83,83,80,83,87,82,84,81,83,84,83,82,82,84,81,85,85,84,82,82,84,82,79,83,81,90,83,82,84,83,84,81,82,82,83,82,85,84,84,91,86,84,84,84,83,83,82,86,84,89,84,81,84,83,84,80,82,81,83,84,82,84,85,82,83,84,86,83,84,84,84,81,86,82,82,82,83,85,84,81,81,86,84,83,83,82,84,82,86,82,81,84,85,83,87,84,89,84,83,82,81,85,82,87,84,87,84,82,81,83,84,84,83,83,82,84,81,84,85,85,82,83,79,82,82,87,84,77,84,84,85,85,83,85,81,85,82,79,82,83,87,83,83,83,85,83,82,82,83,84,82,83,84,82,82,84,88,84,81,84,84,84,81,81,84,82,83,83,84,79,83,82,86,80,84,83,84,82,87,85,87,81,82,84,81,86,86,83,82,84,85,85,83,82,83,89,86,84,84,83,82,83,83,78,85,84,84,85,83,83,82,84,82,80,84,84,84,82,86,80,84,83,82,84,84,84,85,85],"z":[1989,2018,2017,2012,1961,2018,1985,2008,1999,2011,1969,2006,2000,2017,2007,2018,2002,1982,2014,2003,1982,1971,2015,1972,2004,1984,2018,1968,1975,1993,1952,1975,2000,2012,1988,1957,2015,2014,1956,1990,1971,2009,1978,2018,1995,1970,2009,2005,2004,1968,1972,1951,2005,2000,1994,2010,1987,2002,1981,1980,1950,2018,1986,1990,1969,1981,1991,2014,1969,2005,2018,1976,1995,2007,2001,1989,1973,2018,1974,1996,2000,1947,2001,2005,2014,1992,1947,1991,2011,1986,1971,1984,1984,1975,1999,1993,2013,1996,1968,2015,2012,1977,1953,1998,1994,2010,1956,1971,1989,2018,1952,1977,1968,2018,1968,2013,2005,2008,1995,1948,1975,1997,2005,1981,2018,1997,2003,1963,1978,1993,1974,1992,2006,1951,2012,2014,1988,2012,2003,2016,2014,2001,1992,1962,1989,2012,1972,1975,1997,2012,1979,1952,2009,1972,2001,2012,1994,1968,2002,2018,2002,1947,1989,1988,2012,2007,1994,2018,1992,2004,2014,1972,1951,1989,1994,2013,1950,1951,1962,1997,2017,2000,1996,2017,2005,1979,1968,1973,2014,2008,1986,2015,1972,1950,2018,2017,2009,1948,1996,1964,2016,1948,1969,1994,2018,2003,1981,2010,2011,2007,2011,1972,2007,2015,2009,1992,2013,2018,1971,2006,1974,1947,1971,1959,2002,1986,2018,2015,1953,2001,1986,2016,2018,2006,2016,1999,1980,1995,2015,1995,2000,2003,1950,1954,1969,1976,1947,2018,1980,2014,2011,2015,1983,1994,2006,1987,2000,2007,1984,1998,1981,1998,1982,2018,1992,1951,1998,1984,2001,2018,2018,2003,2012,2018,1953,1997,2018,2007,1995,1987,1976,2001,1992,2008,1998,2018,1969,2001,2018,2013,1968,1999,2009,1956,1950,2012,2004,2011,1997,2016,2002,2012,1988,1949,1994,2010,2002,2008,2018,2014,1996,2000,2009,2014,2005,2006,1984,1955,1972,1988,2010,1994,1971,1974,1972,2018,2018,1950,1965,1985,1980,2018,1995,2010,2011,1996,2017,2014,1993,2013,2002,1991,2007,2017,2006,1953,2003,1978,2018,2018,1997,1959,1976,1972,2010,1968,2016,1996,2001,2016,2008,1975,1951,2013,1984,2014,2016,2017,2006,2018,2008,2007,1950,2013,1974,2005,2015,2005,1993,1974,1981,1973,2006,2001,2007,2003,1969,1999,1950,2000,2003,1995,2004,1990,1949,1975,1969,2003,2016,1950,1998,2003,2009,2005,1985,2007,1952,1999,1978,1950,2002,1999,2006,1960,1991,1999,1947,2011,2009,2016,1952,1979,2016,2005,1970,2004,1994,1973,2000,1992,1971,1997,2002,1968,1958,1949,2004,2005,2015,1988,1998,1968,2017,1968,2005,1970,2009,1997,2001,2001,2017,1972,2014,2018,1970,2017,1973,2004,2007,1990,2014,2018,1987,2002,1976,1992,2009,2004,1999,1981,2018,1988,1977,1988,2012,1947,1987,1990,2000,1994,1997,1976,2006,2018,1968,1971,1999,2018,1976,1970,1994,1962,2000,2013,1988,2005,1998,2017,1983,2018],"type":"scatter3d","mode":"markers","name":"C","marker":{"color":"rgba(102,194,165,1)","line":{"color":"rgba(102,194,165,1)"}},"textfont":{"color":"rgba(102,194,165,1)"},"error_y":{"color":"rgba(102,194,165,1)"},"error_x":{"color":"rgba(102,194,165,1)"},"line":{"color":"rgba(102,194,165,1)"},"frame":null},{"x":[235,210,243,225,265,205,270,220,260,220,240,225,210,230,225,185,220,255,250,220,235,265,220,257,215,250,250,228,220,225,265,218,220,220,232,225,230,220,230,270,230,230,230,215,225,235,205,215,222,220,230,225,225,210,220,250,240,200,240,205,230,215,230,210,255,220,225,240,235,200,215,235,240,250,195,250,245,220,230,229,225,235,205,235,245,210,215,235,280,289,240,205,235,245,250,217,235,205,200,245,235,230,215,250,230,230,220,225,220,225,265,245,225,240,220,230,255,234,185,240,215,210,230,210,228,225,235,215,210,230,225,230,203,250,265,225,205,230,220,225,222,218,228,195,219,245,252,275,249,238,255,215,215,235,230,235,190,220,260,245,249,220,190,210,220,225,215,235,225,200,231,230,235,185,185,220,245,225,240,220,240,228,235,235,250,200,210,230,230,222,235,225,225,255,225,230,260,245,226,225,215,215,230,250,244,243,230,240,245,210,210,230,220,230,230,242,235,240,210],"y":[81,81,82,82,81,80,82,79,83,80,84,83,80,83,81,78,81,81,81,80,85,82,82,81,82,79,83,79,83,84,82,81,83,78,84,80,82,82,84,83,81,81,79,82,81,80,80,78,81,82,82,84,81,82,81,84,80,77,84,82,80,81,82,79,83,82,78,83,84,82,80,82,82,83,82,83,85,81,83,83,81,82,80,83,82,79,78,81,82,82,82,83,82,83,82,83,83,82,77,78,84,81,78,84,80,84,82,82,83,80,83,85,80,84,80,82,81,81,80,82,82,79,82,81,83,81,83,82,77,80,80,76,80,84,83,81,83,80,81,79,79,82,83,80,81,82,82,83,83,84,82,82,85,83,80,83,79,78,82,83,83,83,79,78,78,82,81,81,82,81,81,83,82,81,77,83,83,82,82,81,81,88,83,83,81,78,84,83,83,80,81,81,80,82,81,83,83,82,82,83,83,78,80,83,84,83,80,82,79,78,83,82,82,83,79,82,82,84,76],"z":[1978,1988,2018,1969,2002,1968,2003,1970,2015,1957,1992,1979,1971,2012,1977,1949,2018,2018,2018,1951,1995,1997,1983,1997,1985,1966,2007,1958,2013,1991,1997,1985,1982,1958,2018,1964,1985,1992,1976,2018,1983,1973,1971,1976,1975,1976,1958,1951,1971,1983,1983,1996,1981,1976,1984,2018,1969,1949,2002,1984,1969,1962,1977,1969,2018,1980,1949,2018,1991,1980,1970,1968,1998,2006,1982,1994,2017,1984,1987,2018,1953,2017,1960,1993,2018,1958,1949,1985,2010,2018,1988,1986,1991,1983,2018,1990,1986,1963,1947,1957,1986,1966,1950,1996,1964,1982,1985,1982,2018,1974,1997,2018,1974,1998,1971,1983,2017,1964,1959,1999,1995,1949,2018,1986,1978,1970,1991,1985,1953,1954,1954,1947,1947,1991,2018,1975,1977,1974,1994,1979,1958,1990,2018,1950,1954,2011,2013,2018,2012,2018,2014,1983,1993,2004,1968,1985,1973,1949,1994,2018,2018,2004,1950,1949,1955,2011,1965,1974,1975,1958,1976,1986,1984,1957,1948,2002,1998,1976,1993,1975,1996,1992,2017,1999,1997,1953,1993,2009,1991,1956,1973,1977,1975,2018,1971,1995,1994,1997,1991,1977,1984,1950,1970,1997,2018,2018,1962,2018,1981,1950,1987,2000,1989,1986,1979,1999,2012,2018,1947],"type":"scatter3d","mode":"markers","name":"C-F","marker":{"color":"rgba(252,141,98,1)","line":{"color":"rgba(252,141,98,1)"}},"textfont":{"color":"rgba(252,141,98,1)"},"error_y":{"color":"rgba(252,141,98,1)"},"error_x":{"color":"rgba(252,141,98,1)"},"line":{"color":"rgba(252,141,98,1)"},"frame":null},{"x":[223,225,220,195,210,240,210,245,230,217,245,240,230,205,220,230,195,220,225,230,220,220,220,195,200,240,190,225,205,240,232,210,250,215,230,220,205,235,235,205,235,240,225,220,232,208,210,215,195,210,252,210,205,226,205,205,195,190,250,215,225,220,210,200,260,225,235,200,237,235,205,205,185,224,210,225,202,245,245,235,200,210,220,235,210,205,215,210,235,210,220,195,240,250,210,215,235,240,220,205,235,220,192,215,235,228,226,215,220,210,225,225,245,185,215,195,230,210,215,190,215,230,245,275,195,215,205,195,195,175,255,190,200,220,245,205,214,200,175,225,190,220,270,190,220,200,210,208,210,205,209,215,190,260,220,242,225,215,228,220,205,215,170,235,175,218,255,210,180,224,275,195,245,205,220,215,220,215,230,225,220,230,250,239,190,188,185,230,225,225,195,190,233,250,225,232,224,200,210,198,212,235,230,225,210,235,255,210,210,193,205,234,210,230,210,239,180,245,225,235,215,215,235,210,200,215,233,235,240,210,235,220,230,198,220,190,200,214,215,235,230,240,240,215,215,215,220,240,220,235,220,230,205,190,225,250,215,220,210,175,230,215,220,220,220,215,218,230,190,180,210,220,250,175,230,268,200,198,200,210,215,175,220,200,209,188,210,200,190,190,225,190,210,215,225,200,205,210,220,215,275,220,220,210,245,205,197,185,240,230,245,190,185,205,210,195,220,220,202,200,245,235,210,205,185,228,210,244,185,235,190,225,190,230,210,205,220,215,175,262,215,225,170,220,275,228,215,225,210,260,210,219,220,220,205,205,210,225,240,195,175,240,230,250,225,215,245,245,205,195,205,225,190,210,205,238,200,230,215,220,200,205,225,185,215,205,225,190,235,210,185,250,250,220,220,245,185,225,220,215,222,254,195,195,210,223,215,240,235,240,230,206,230,227,235,215,210,190,220,226,195,205,215,180,251,190,238,230,220,240,190,190,195,210,225,230,230,220,210,220,205,215,195,200,250,195,246,195,220,225,231,230,200,239,240,235,220,242,205,210,220,225,219,225,220,235,210,215,226,220,210,230,215,225,210,210,205,195,220,200,233,225,240,230,200,225,185,195,220,210,215,188,222,230,190,220,230,220,230,250,205,204,240,220,225,210,230,235,215,235,260,240,225,208,175,215,210,235,246,190,210,210,210,193,253,215,215,215,200,175,210,180,220,212,223,260,185,218,233,230,220,231,235,240,210,240,230,190,245,201,230,221,250,200,220,240,250,205,205,190,200,215,245,240,210,175,210,215,215,203,221,190,220,190,205,218,251,225,235,250,210,230,252,225,205,220,198,210,200,190,213,218,230,225,172,230,190,198,215,210,205,215,210,210,235,232,225,205,215,220,230,225,220,190,210,210,235,220,245,220,215,210,215,240,225,203,215,203,220,215,230,200,192,232,220,215,225,190,220,190,227,248,230,230,220,215,185,234,210,222,225,245,190,200,230,228,210,210,215,215,205,225,215,185,225,240,250,225,220,215,251,215,205,220,205,215,234,218,215,215,210,227,235,240,185,218,202,210,205,200,250,230,215,210,195,220,230,215,230,218,200,205,212,220,239,234,240,250,224,220,220,190,250,260,205,200,215,266,225,205,210,230,230,244,240,230,195,200,205,225,210,205,240,240,220,225,215,200,215,200,221,215,205,200,210,235,240,200,175,250,225,240,215,220,235,210,210,195,225,190,230,235,215,205,210,210,190,215,230,246,215,220,215,210,205,216,235,215,190,210,200,230,220,220,205,215,215,180,215,210,229,235,245,221,205,195,195,238,249,185,225,230,220,175,225,236,225,225,235,245,185,210,221,230,238,240,230,195,215,220,200,238,210,225,245,220,230,216,250,225,210,225,230,185,225,180,215,220,225,245,205,222,190,228,200,205,215,210,220,215,205,241,225,210,195,175,225,210,210,205,210,210,245,210,200,225,210,224,240,210,195,222,225,250,210,235,230,215,220,238,230,224,220,245,220,220,232,210,218,195,225,220,185,195,245,230,220,220,235,218,198,205,230,200,220,240,225,215,235,238,190,212,245,235,220,227,235,210,205,190,213,200,235,205,240,215,215,210,195,240,205,210,250,247,210,232,230,170,215,270,225,215,200,235,195,175,215,214,240,220,225,210,212,200,190,237,217,230,210,220,195,235,235,219,250,190,185,212,225,220,210,230,228,205,246,225,215,220,260,240,225,210,215,190,215,223,225,210,195,241,208,185,200,173,200,205,200,220,240,229,180,237,210,230,188,210,210,198,285,225,190,220,245,200,194,165,210,217,215,200,230,215,190,225,255,235,210,248,195,228,230,216,210,255,220,215,238,210,250,180,220,180,195,225,225,225,185,225,230,195,205,230,235,225,215,248,225,215,250,200,218,200,210,195,188,230,215,185,205,225,210,270,185,220,239,220,205,210,220,195,215,210,210,200,260,220,215,260,230,210,235,220,250,210,215,275,225,230,225,255,244,210,260,205,225,220,220,260,242,220,215,210,200,256,225,215,235,205,265,261,230,235,225,215,220,230,215,245,195,225,225,220,205,205,225,190,218,210,192,210,210,284,250,206,190,225,190,205,220,185,245,249,236,220,220,200,245,215,221,210,220,210,215,220,230,240,230,215,240,195,215,232,220,225,195,240,240,210,224,220,210,210,240,190,215,225,220,220,195,235,210,230,219,210,190,210,230,230,240,195,190,232,180,230,230,200,250,190,251,200,204,240,238,210,270,240,210,215,195,221,215,200,195,220,200,230,240,220,235,200,210,218,206,260,225,205,205,237,255,225,190,205,210,225,250,220,215,218,195,200,245,195,215,234,230,200,200,210,240,215,256,210,225,225,200,210,210,270,220,227,235,221,210,215,260,225,225,226,220,225,215,215,260,215,220,213,220,221,210],"y":[78,81,79,75,78,79,78,79,79,80,80,79,80,81,80,78,78,81,83,80,81,81,81,80,79,82,79,79,79,80,80,76,83,80,81,77,77,81,82,81,81,81,81,81,83,80,80,79,76,78,78,80,75,79,75,79,77,79,80,81,80,80,78,77,80,77,78,75,82,81,79,79,77,81,78,85,83,80,80,78,79,79,80,81,80,80,80,82,80,78,81,75,82,78,78,79,83,81,81,77,81,80,77,80,82,80,78,80,80,77,79,80,82,79,79,77,82,80,78,78,80,80,80,80,79,79,78,75,74,76,79,76,78,79,81,76,79,81,74,79,78,79,83,75,80,75,78,78,79,78,79,82,78,80,77,80,78,80,79,79,79,79,73,83,79,81,80,79,78,79,81,79,80,79,79,80,80,80,80,81,80,78,81,81,78,78,77,82,80,79,79,74,82,81,82,79,81,76,78,79,78,81,82,80,80,82,82,77,80,77,81,81,80,80,77,81,78,81,79,80,81,78,81,77,80,75,79,81,82,79,78,81,80,72,81,77,76,80,80,81,82,82,81,75,79,79,80,82,79,80,78,82,79,77,78,81,79,83,80,75,81,77,81,80,81,80,79,78,75,75,77,79,80,77,79,80,76,79,80,81,79,76,81,79,79,77,79,79,79,80,78,75,80,81,78,81,80,78,78,80,81,79,79,74,83,80,81,77,80,77,80,79,76,78,79,78,75,80,80,81,80,80,77,80,73,80,79,81,77,83,78,81,75,82,79,77,80,77,74,81,79,80,75,79,81,79,81,81,79,79,77,82,80,79,79,79,81,79,82,74,74,81,81,81,82,78,81,81,80,75,77,81,79,78,80,81,79,80,79,81,80,82,81,81,78,74,78,79,80,80,73,79,82,82,81,81,75,79,80,78,81,81,75,80,80,81,79,79,79,80,78,79,79,81,81,80,78,79,79,83,77,80,79,77,82,79,79,81,77,82,76,79,75,81,79,82,80,79,80,80,77,81,80,79,81,80,80,79,79,82,79,81,82,80,78,81,80,81,75,77,79,78,78,80,78,81,80,79,80,81,77,81,81,81,80,79,79,80,81,79,79,79,81,79,76,81,76,78,79,79,78,80,80,79,80,79,81,81,80,77,80,78,81,79,81,79,79,81,80,80,79,83,80,80,75,78,80,82,80,81,80,82,80,79,81,79,79,83,79,75,80,76,80,79,80,80,75,81,79,83,79,82,82,84,82,81,82,79,81,81,80,82,81,79,81,80,78,83,80,82,78,80,79,80,80,79,81,79,80,79,80,79,80,80,79,80,80,81,83,80,81,82,81,76,80,80,79,79,77,75,80,78,81,79,74,83,79,78,78,78,81,79,79,81,81,79,81,79,80,78,81,78,81,79,79,81,81,82,80,79,79,81,77,81,81,81,80,75,80,79,82,75,82,81,81,81,83,78,77,74,79,81,79,78,83,80,75,81,81,82,79,81,74,78,79,82,80,77,79,82,80,81,78,77,81,80,81,80,77,80,82,81,78,75,78,82,82,80,79,79,77,82,82,81,77,78,80,79,74,79,81,82,79,79,78,79,84,79,79,81,79,79,81,79,82,81,80,79,79,81,78,76,80,79,80,76,79,81,80,79,75,80,81,78,80,82,77,83,79,80,80,78,80,80,81,79,78,79,80,77,80,77,77,74,79,83,82,80,75,82,82,81,78,81,80,79,81,75,81,75,82,80,78,77,79,81,74,78,82,80,78,82,79,78,79,78,80,79,76,80,78,80,80,77,80,77,81,77,79,80,80,81,82,81,80,79,80,81,83,77,81,82,81,74,77,79,79,78,81,80,75,78,81,78,81,80,81,80,77,78,81,79,78,78,81,79,80,80,81,78,79,79,78,76,79,75,80,79,82,84,79,80,76,79,79,77,78,75,82,78,77,79,80,79,75,80,82,78,80,79,80,81,79,79,77,79,79,81,81,77,77,81,80,80,77,79,82,81,80,81,81,77,78,79,79,80,81,77,79,77,79,80,75,81,82,80,80,79,82,79,80,79,83,77,77,80,81,79,78,79,75,81,82,80,82,82,80,77,76,79,80,76,80,82,82,80,80,77,77,80,77,79,80,81,78,80,78,74,79,81,81,78,76,81,80,75,79,78,81,81,79,78,79,80,79,82,80,79,79,79,79,79,82,77,79,76,76,80,79,81,80,79,82,78,81,79,80,81,81,79,80,78,81,77,81,82,79,79,77,81,80,72,77,74,77,77,77,80,81,80,78,80,77,77,79,80,78,81,81,81,77,79,81,80,74,74,79,81,78,78,81,79,75,78,81,81,79,81,79,80,80,80,80,81,78,79,82,78,79,75,82,78,77,81,82,81,79,82,80,80,78,79,80,80,75,81,80,80,82,80,78,76,78,74,77,79,83,73,79,79,79,82,75,78,80,80,77,77,80,79,76,81,81,77,82,80,79,81,80,76,79,80,80,78,76,80,81,77,79,81,79,78,82,80,79,81,80,81,81,80,78,79,79,81,80,78,80,78,81,79,81,80,81,78,80,82,81,82,79,80,82,80,76,77,81,80,80,81,74,78,79,80,80,78,77,84,80,78,80,79,78,82,81,82,79,79,80,78,81,79,82,81,80,80,81,81,81,81,83,78,81,83,79,80,78,81,82,79,80,78,75,80,81,79,79,80,78,80,76,80,79,80,81,80,79,78,82,82,78,79,77,80,76,81,77,79,81,80,81,80,80,80,81,80,80,81,76,76,78,82,79,81,79,82,78,78,80,80,79,81,77,81,81,82,82,81,79,81,80,80,79,78,80,81,81,78,78,79,76,79,79,78,80,82,79,78,80,79,82,80,80,78,79,80,80,77,80,82,83,81,79,80,79,81,78,81,83,80,80,80,81,78,79,79,81,79,78,80,80],"z":[2003,2008,1981,1948,1968,2018,1977,2015,1968,1991,2016,1994,2010,1969,1990,1972,1972,1981,1997,1997,2018,2016,1994,1985,1979,2018,1955,1992,2016,2018,2018,1962,2004,2018,1988,1956,1974,2018,2008,1984,2000,2016,2018,1976,2006,2012,1991,1989,1947,1957,2000,2018,1969,2017,1947,1980,1951,1976,2017,2009,2003,2014,1993,1974,2006,1972,1968,1951,2004,2018,1973,1971,1976,2018,2018,2018,2010,2015,2017,2000,1982,1992,2001,2017,1970,1989,1989,2018,1987,1959,1992,1949,2018,1993,1985,1993,2014,2004,2001,1954,2018,1962,1968,1996,2016,2018,1999,1971,2000,1954,1978,1980,2002,2009,2010,1975,2012,1971,1982,1980,1976,1996,2005,2016,1968,1998,1959,1955,1947,1947,2012,1971,1994,1988,2009,1950,2002,2005,1949,2012,1958,1980,2013,1947,1990,1952,1990,1969,1963,1965,2016,2002,1979,1994,1952,1996,1965,1973,2016,2012,1970,1983,1947,2006,1964,2018,2003,1980,1991,1993,2011,1973,2012,2011,1987,2018,1969,1977,1973,2018,1993,1972,1986,2018,2001,1974,1974,1989,2018,1986,1991,1951,2018,2017,2015,2016,2015,1969,1976,1975,1991,1994,2005,1979,1988,2018,2018,1949,1984,1968,1989,2012,1978,1986,1956,2016,1982,2018,1980,1997,2018,1979,2004,2009,1976,1947,1989,2009,1986,1978,2018,2000,2018,1947,2001,1952,1949,2005,2015,2001,2009,2015,2000,1947,1973,1990,1977,2018,1980,2012,1977,1983,1981,1980,2016,2012,1995,2015,1969,1947,2018,1989,2018,1984,2018,2008,1978,1976,1947,1950,1972,1972,2012,1950,1981,2015,1972,1972,1963,1990,1975,1947,2016,1996,2011,1972,1995,1986,1975,1982,1954,1954,2016,2013,1978,2005,1985,1975,1970,1994,2005,1996,2014,1947,2018,2001,1980,1960,2003,2012,1989,1991,1971,1975,2018,1979,1958,1999,1980,2016,2015,2011,2012,1970,1949,2018,1966,2000,1947,2008,1963,2006,1947,2003,2015,1968,2018,1972,1948,2006,1978,1983,1963,2012,2004,1973,1982,2006,1996,2007,1977,2002,2005,1976,1973,1992,1971,1974,2007,1947,1947,2004,2005,2006,2018,1970,2008,2001,1968,1949,1976,1986,1984,1977,1984,2008,1974,2018,2013,2018,1991,1986,2018,2010,1970,1947,1971,1950,1986,1972,1947,2014,2016,2002,2018,2015,1950,2011,1989,1996,2015,2006,1951,1999,2018,1994,1976,2000,1997,1977,1989,1972,2018,2018,2018,1986,1987,1973,1979,2012,1965,1988,1983,1954,2018,1978,2010,1998,1963,2005,1949,1963,1947,1977,1975,2010,2007,2005,1971,2002,1972,2001,1975,1953,2016,1998,2012,1982,1968,2017,2009,2014,1975,2014,2014,2018,2005,2003,1950,1969,2010,2013,1981,1996,1957,2007,1987,2002,1999,2000,1971,2018,1999,2009,1971,1975,1979,1971,1991,1995,1974,2017,2004,1968,1949,2006,1952,1979,2018,1971,1959,2013,2000,1968,1956,1968,2012,2008,1990,1996,1995,1993,2013,1979,1998,1971,2018,2000,2015,2005,2005,2010,2010,2018,1948,1971,1989,2018,2016,2018,1958,2018,1969,2018,2011,2008,1976,2000,1975,1947,1979,1951,1998,2002,2014,2002,1950,2016,2018,2013,1997,2018,2015,2012,2005,2008,2018,1993,2000,2008,2013,2012,2018,1982,1988,1986,2001,1981,2009,1986,1982,1961,2018,1987,1990,1989,1986,2008,1989,1975,2013,2018,1998,1984,1969,2007,2013,1985,2015,2004,1989,2014,2017,1952,1978,1976,1981,2013,1969,1953,2012,1982,2001,1987,1948,2017,1985,1975,2012,1971,1983,2001,1968,2008,1994,2018,1980,1993,1999,1955,2001,1985,2015,1970,1969,1962,1987,2018,2013,1971,1972,1982,1975,1985,1991,2007,1969,1949,1976,1968,1984,1949,2006,2009,2018,2018,2018,1969,1975,1947,2004,2016,2010,1993,2004,2008,1951,2011,2018,2018,1969,2017,1947,1969,2018,2018,1995,1997,2004,2014,1994,1984,1970,1953,1989,1991,2003,2003,1964,1977,2018,1975,1963,1947,2018,2018,2018,2005,1970,1971,1974,2012,2001,2009,1951,2013,1983,1971,1954,2007,2004,1980,1973,1976,1969,2015,2018,1972,2003,2009,1974,1988,1986,2015,2018,2015,2004,2003,2010,2005,1968,1951,1994,2015,1988,1975,1983,2010,1977,1981,1950,2018,2018,1998,1990,2006,1952,2018,1998,2018,1989,1973,2007,1972,2013,1975,1970,1987,2018,1953,2001,1979,1962,1948,1988,1987,2017,1973,1948,2007,1991,2011,1971,1985,2018,1971,2009,1947,2005,1949,1984,2018,1981,1971,2018,2015,1947,2003,2001,2018,1973,2018,1988,2002,1989,2014,2014,1983,1953,1978,1954,1968,2006,1963,2012,1953,1988,1957,1968,1999,1993,2018,2018,2006,2010,1995,1979,2018,2014,1951,1991,2014,1988,1947,1988,2006,2004,1970,1998,1999,1953,1955,2008,2018,2006,2012,2018,1979,1968,1990,2017,1993,1976,2002,1998,2008,2017,2009,2017,1981,1990,2012,2007,1952,1998,1951,1997,1978,2017,2018,2014,1997,1949,2016,1975,1970,2018,1953,2013,1971,1971,2018,1987,1980,1950,1988,1990,1962,2018,2018,2008,2014,2003,1978,1975,1992,2012,1997,2007,1949,1968,2001,2016,2017,1969,1968,2018,1990,1981,2000,2018,2008,1974,2004,1978,2000,2018,1956,2011,1950,1983,1972,1952,1997,2007,1984,1986,1986,2005,2001,2018,1969,2018,1973,1968,2011,2014,2008,2007,2018,1953,2016,1993,1992,2018,2013,1962,1958,1952,1983,1995,1961,1995,2014,2015,1985,1983,1974,1954,2007,1967,1952,2003,2001,1968,2012,1988,1947,2004,2010,1960,1968,1951,1971,1976,1949,2001,1968,2007,1992,2005,1982,2001,1975,1972,2017,1981,1982,2000,1997,1976,2005,2000,1970,2009,1959,1947,1990,1979,1990,1998,1979,2017,1965,2009,2006,1985,1968,2013,1973,1993,1973,1972,1956,1985,2018,1999,1978,1951,2012,1984,1948,1976,1949,1950,1954,1958,1970,2017,2000,1997,2018,1970,1968,1988,1978,1976,1964,2017,2005,1970,1964,2009,1958,1947,1947,1982,2014,1979,1976,2018,1973,1972,1971,2007,2009,1997,2002,1969,2018,2014,2012,1985,2012,1963,2003,2007,1991,2012,1947,1996,1954,1976,1983,2011,2018,1976,1995,2001,2001,1973,1971,2007,2005,1954,2011,1973,2014,2007,1970,1960,1950,1994,1947,1968,1986,2000,1951,1964,1997,2000,2016,1960,1971,1998,1997,1957,1963,1993,1972,1974,1971,2003,1964,1989,2001,1981,2017,2013,1954,1970,1959,2018,1954,1963,2007,2009,1995,2011,1996,2009,1972,2006,2018,2015,2000,1990,2007,2018,1975,1977,1986,2014,2011,1991,2001,2006,1971,2006,2010,2013,2018,2015,1976,1976,2010,2015,2012,1992,1983,1966,2011,1949,1972,1989,1978,1981,1980,1949,2003,1973,2005,2004,1975,1959,2006,1972,2010,1995,1957,2018,2015,2000,2015,1973,1968,1992,2011,2017,1981,2006,1976,1996,1993,2014,1999,2001,1987,2014,1993,1992,2016,1990,2008,1973,1990,2018,1988,2008,2015,1962,1995,2006,1984,2015,2004,1972,2018,1958,2013,1969,2018,2013,1976,1999,1967,2015,2015,2005,1980,1972,1996,1949,1984,1998,1975,2018,1968,2014,1989,2018,1994,2005,1987,2014,1996,1968,1962,1969,2013,2018,1982,1983,1985,1971,1957,2017,2007,1970,1986,1975,2011,2005,2012,2008,1994,2009,2018,1990,2003,1987,2017,1985,2015,2012,2013,1999,2018,1949,1971,2007,1971,1968,2018,2018,1970,1988,1996,2017,1964,1998,1976,2018,1988,1986,1978,1971,2003,2017,1997,1982,2006,1968,1994,2017,1994,1988,2014,1993,2011,1969,1975,2018,1972,1982,1999,2013,2018,1980],"type":"scatter3d","mode":"markers","name":"F","marker":{"color":"rgba(141,160,203,1)","line":{"color":"rgba(141,160,203,1)"}},"textfont":{"color":"rgba(141,160,203,1)"},"error_y":{"color":"rgba(141,160,203,1)"},"error_x":{"color":"rgba(141,160,203,1)"},"line":{"color":"rgba(141,160,203,1)"},"frame":null},{"x":[240,220,240,260,234,260,255,245,230,240,252,215,235,220,215,250,235,200,245,200,210,225,270,225,185,215,200,270,207,190,237,258,200,235,220,220,245,240,215,210,240,228,225,185,245,210,220,200,250,224,265,195,200,225,195,240,220,185,240,230,210,220,195,195,255,224,190,205,215,260,200,230,210,210,235,253,215,230,237,289,225,212,230,205,235,225,250,195,195,250,240,270,225,210,205,265,275,190,240,236,225,250,210,190,195,210,205,200,240,250,220,225,198,230,225,203,220,195,235,215,220,200,210,220,222,225,220,205,225,180,190,210,225,220,240,235,195,225,235,235,210,240,235,225,218,225,220,195,242,192,250,215,210,200,245,220,225,215,215,230,235,210,200,235,240,220,210,240,236,210,230,240,220,205,220,218,215,245,250,210,225,220,225,220,242,240,220,230,245,205,215,230,277,200,220,230,215,212,203,220,215,230,220,235,240,215,220,225,185,205,215,235,215,210,200,200,230,225,220,230,215,248,216,205,230,250,220,235,215,220,255,235,210,205,185,230,215,210,210,195,215,195,208,215,230,250,190,235,238,195,220,222,245,215,240,238,205,225,200,220,257,226,250,225,220,245,215,220,180,224,219,237,225,235,200,235,205,230,215,185,200,233,220,235,220,240,220,240,210,225,250,260,190,220,225,215,260,190,218,200,225,225,225,205,195,250,265,220,240,230,235,220,220,210,214,250,215,225,240,230,235,215,220,230,245,215,245,200,220,263,232,245,215,200,215,250,238,225,225,240,220,235,240,210,205,215,230,273,205,205,220,205,240,225,220,210,230,220,215,227,255,245,290,230,250,225,220,220,260,215,215,240,235,200,230,220,205,230,245,215,218,210,220,225,260,215,253,250],"y":[82,83,82,83,82,81,82,82,82,82,82,80,83,81,83,81,81,81,84,78,80,80,82,81,81,81,77,79,81,78,82,81,77,83,81,80,82,83,77,81,81,78,83,81,81,81,77,80,82,81,80,77,77,81,76,84,82,75,80,82,77,83,77,79,83,82,77,81,82,81,79,81,78,81,79,82,81,83,83,81,81,78,82,80,81,81,80,77,78,83,82,81,81,81,77,82,82,77,83,83,82,82,80,77,78,78,76,77,83,84,82,80,77,81,76,74,82,79,84,82,81,77,79,81,81,79,82,81,82,79,78,79,80,80,80,81,79,83,80,82,80,78,81,80,79,79,80,78,81,80,83,81,81,80,82,80,80,81,80,81,81,79,78,82,81,80,80,81,77,79,78,83,79,81,80,79,81,84,83,82,82,78,81,82,84,80,81,82,82,77,78,83,81,82,78,83,81,79,79,81,80,81,78,83,83,80,79,78,79,82,82,82,79,79,77,77,83,80,81,80,81,81,85,76,82,82,81,83,81,81,82,80,82,81,78,79,83,77,78,81,80,77,79,80,79,84,76,82,82,74,80,84,83,80,83,82,82,78,75,81,81,83,82,80,80,82,77,79,76,80,80,82,81,81,81,82,81,78,81,76,79,81,82,81,80,87,79,83,85,83,81,81,77,82,81,79,82,80,82,80,82,79,82,80,77,80,83,81,83,83,83,79,80,82,81,82,81,82,80,82,81,80,79,82,84,80,83,79,82,81,79,82,83,80,79,83,81,82,81,81,77,79,80,76,80,79,81,82,76,76,82,78,81,82,81,78,80,83,79,81,81,81,81,79,83,80,82,81,80,80,83,81,80,81,82,84,80,83,85,81,79,82,80,83,83,79,84,83],"z":[1995,1993,2015,2018,2018,2017,2011,2017,1998,1990,2018,1978,2014,1988,1999,2016,1991,1982,2016,1955,1980,1980,2007,1974,1980,1975,1952,2016,1976,1949,2010,2015,1950,2016,1984,1970,2006,2018,1955,1982,1997,1975,2008,1983,2003,1963,1952,1972,2007,2000,1998,1947,1951,2000,1950,2018,1998,1950,1972,2000,1955,2004,1952,1958,2011,2000,1948,1996,1988,2018,1950,1991,1976,1997,1970,2018,2006,2007,2018,2015,2001,1973,2005,1962,1999,1982,2017,1950,1951,2016,1997,2005,1996,2001,1950,2018,2018,1949,2003,2012,1994,2015,1955,1954,1950,1958,1947,1952,2016,2018,2002,1996,1950,2000,1951,1948,1976,1962,1991,2004,2001,1973,1975,1993,1991,1974,2007,1983,1995,1976,1960,1957,1965,1982,2018,2008,1954,2003,2018,1993,1976,2016,1984,1983,1965,1955,1971,1948,2016,1972,2018,1980,1991,1957,2018,1982,1972,1972,1989,1976,2017,1973,1958,2018,1972,1980,1981,2018,1953,1986,1973,2003,1973,1984,1976,1963,1998,2018,2010,1983,1986,1977,1978,1993,2018,1975,1969,2003,1998,1977,1953,1994,2001,1975,1975,1997,1969,1950,1983,1997,1978,1986,1978,2005,2008,1984,1969,1973,1954,1976,1989,1996,1949,1974,1960,1954,1998,1974,2018,1974,1988,1994,2018,1950,2003,2011,1973,2004,1987,2011,2016,1982,1993,2002,1952,1972,1986,1951,1952,1979,1976,1952,1958,1980,1959,2013,1951,2005,2018,1950,1958,2017,2013,1972,2018,1994,1994,1966,1947,1976,2018,2014,2018,2004,1970,2017,1955,1950,1949,1961,1972,2018,1983,2001,1996,1992,1965,1963,1993,1955,1953,1978,1992,1987,1978,2018,1975,2018,2018,1997,2018,2018,1950,2018,1982,1958,1989,1975,1997,1977,2007,1985,1988,1987,1949,1990,2003,1962,2018,2000,2007,1966,1964,1989,2001,1997,1972,1999,1986,2005,1981,1972,1980,1997,2018,1993,2017,1975,1990,2017,1958,2016,1989,1979,1958,2016,2018,1996,2001,1997,1951,1995,2018,1950,1977,1973,1996,2017,1947,1950,2006,1952,2012,2013,1977,1976,1988,1982,1973,1979,1993,2008,2005,1970,2016,1981,1993,2008,2017,1998,1999,1999,1995,2000,2005,2007,1984,1999,2008,1954,1971,2018,1976,2009,1998,1955,2018,2018],"type":"scatter3d","mode":"markers","name":"F-C","marker":{"color":"rgba(231,138,195,1)","line":{"color":"rgba(231,138,195,1)"}},"textfont":{"color":"rgba(231,138,195,1)"},"error_y":{"color":"rgba(231,138,195,1)"},"error_x":{"color":"rgba(231,138,195,1)"},"line":{"color":"rgba(231,138,195,1)"},"frame":null},{"x":[210,215,232,200,230,205,215,208,222,190,205,180,205,215,190,200,185,215,210,205,185,186,210,210,210,185,210,225,205,185,220,210,236,215,175,195,180,215,205,210,190,200,205,210,195,208,200,195,195,220,220,200,189,205,225,230,240,200,189,198,175,200,195,210,175,190,190,209,180,220,230,195,210,195,200,210,175,205,218,200,185,200,200,200,210,215,203,226,205,215,225,180,245,210,210,215,170,226,200,207,218,200,250,200,185,215,195,206,215,218,215,218,195,190,170,200,195,205,200,185,190,195,205,210,195,220,205,185,200,215,200,190,220,215,190,185,210,195,234,218,215,215,223,200,185,190,207,220,205,205,200,200,165,185,200,195,185,235,210,215,210,215,190,220,195,205,185,180,205,206,218,190,200,210,205,185,192,185,195,185,210,200,195,190,195,175,195,190,220,185,195,195,210,190,190,220,170,210,215,202,195,195,212,200,215,199,190,225,200,215,190,210,219,205,190,220],"y":[77,79,78,75,81,78,79,78,83,76,80,74,76,79,76,80,75,79,76,77,79,81,77,77,79,76,79,79,77,78,78,80,80,79,75,77,75,79,78,76,78,77,76,77,78,77,79,78,79,80,78,76,79,78,79,81,81,76,75,75,78,74,77,79,75,73,75,79,74,77,79,72,77,79,80,77,71,77,78,78,74,77,78,77,76,81,77,80,77,80,80,75,81,79,77,77,74,80,78,80,80,76,80,75,75,77,78,78,79,79,79,80,79,78,74,76,78,80,76,75,74,74,78,77,75,79,79,75,79,76,78,74,79,81,78,77,80,77,80,80,77,79,78,78,74,79,79,80,79,76,75,78,72,74,78,80,76,79,80,80,79,77,75,78,78,80,77,75,77,79,77,76,78,78,75,76,74,79,76,75,79,78,77,75,77,74,78,77,81,74,77,79,78,73,79,78,76,78,79,77,79,75,78,77,79,80,78,78,79,77,79,79,80,81,77,79],"z":[1975,1997,1994,1960,2018,2002,1994,2006,2018,1962,2006,1949,1957,1987,1954,2018,1957,1979,1953,1977,1990,2018,1987,1975,1983,1950,2017,2018,1975,1992,2002,1999,2018,2016,1951,1975,1955,1995,1985,1976,1987,1962,1953,2005,1982,1991,1994,1989,1977,1988,1974,1968,1973,1985,2018,2017,2018,1949,1953,1949,1974,1947,1977,1987,1950,1947,1950,1999,1951,1988,2004,1947,1997,2015,1981,1976,1950,1980,1983,1994,1950,1998,1983,1950,1970,2018,1978,2018,1970,2018,2013,1956,1999,2013,1979,1986,1947,2018,1976,2018,2014,1969,2018,1948,1951,1962,1980,2016,1999,1990,2018,2017,1996,1992,1950,1970,1989,2000,1968,1951,1953,1950,1984,1969,1949,2002,1984,1949,1977,1959,1988,1947,1993,1987,1977,1976,2012,1974,2018,2017,1972,1970,2018,2001,1949,2002,1988,2001,1994,1960,1951,1982,1947,1950,1958,1993,1953,2017,2004,2011,1990,1972,1964,1981,1978,1991,1984,2002,1957,2018,1978,1973,1981,1993,1957,1949,1950,1985,1977,1951,1990,1974,1976,1950,1980,1947,1970,1977,2011,1950,1993,1987,1989,1949,1985,1991,1955,1966,1989,1977,1983,1956,1975,1970,1987,2018,1986,2018,1999,1979,1997,1986,2003,2015,1960,1990],"type":"scatter3d","mode":"markers","name":"F-G","marker":{"color":"rgba(166,216,84,1)","line":{"color":"rgba(166,216,84,1)"}},"textfont":{"color":"rgba(166,216,84,1)"},"error_y":{"color":"rgba(166,216,84,1)"},"error_x":{"color":"rgba(166,216,84,1)"},"line":{"color":"rgba(166,216,84,1)"},"frame":null},{"x":[162,180,185,183,220,209,162,175,210,202,190,175,185,185,205,183,184,192,175,205,225,171,184,215,185,194,185,195,228,168,184,176,185,150,188,191,175,188,170,175,175,202,185,185,190,160,175,137,183,170,170,197,220,225,222,205,185,213,175,175,180,220,202,190,200,194,190,185,185,177,175,180,205,180,195,172,155,163,185,191,195,175,215,210,175,170,200,168,207,185,175,196,170,190,200,204,180,180,185,200,170,190,175,165,182,185,185,185,175,185,190,175,202,180,197,190,185,190,190,170,172,197,205,175,190,180,205,160,200,185,170,190,200,205,136,195,175,200,185,206,185,195,196,175,180,135,207,175,180,165,215,175,180,170,185,185,184,180,180,190,185,180,185,215,178,161,165,175,160,185,220,182,210,155,215,222,160,189,185,190,180,190,205,225,189,160,190,175,200,215,210,190,170,185,191,175,214,200,205,190,180,195,185,190,200,175,170,190,185,175,213,200,205,165,180,145,165,201,195,160,180,210,170,200,207,210,185,212,190,180,215,210,175,190,190,186,185,178,180,190,210,185,180,180,180,185,188,195,210,205,190,200,175,210,175,190,194,185,166,185,205,195,190,175,180,185,196,175,220,205,175,175,165,185,210,180,175,175,206,190,180,195,205,184,190,184,196,175,185,190,185,180,186,165,220,188,175,180,180,200,195,185,165,150,200,195,165,185,180,185,195,175,190,190,185,190,185,180,170,195,205,205,200,170,210,170,175,209,180,160,195,183,170,185,180,195,215,165,175,200,190,180,190,209,185,190,230,189,198,205,190,175,185,185,175,170,195,184,192,190,190,185,175,175,180,170,170,200,210,164,198,175,171,180,196,183,205,175,195,170,180,195,200,155,191,190,185,170,180,210,215,185,180,180,185,185,190,170,190,180,210,170,195,175,180,114,180,190,195,152,170,185,190,180,170,200,177,200,200,200,185,190,175,195,200,194,198,170,175,185,220,170,185,190,180,220,190,185,185,185,176,201,205,180,185,180,175,185,185,200,188,185,200,170,185,180,205,210,190,190,190,180,175,165,175,194,185,175,160,175,170,175,213,210,195,191,170,200,195,185,185,195,185,170,180,195,185,195,170,205,185,185,200,220,225,190,180,170,156,186,190,185,185,183,160,205,200,187,225,190,190,216,190,185,180,215,190,195,205,175,228,182,205,170,200,200,215,185,180,200,185,180,195,174,185,215,220,190,185,140,195,200,210,185,210,185,185,170,177,185,200,208,175,190,190,185,180,215,184,180,195,191,180,180,170,185,170,220,180,193,160,180,180,175,210,203,190,205,205,175,205,220,175,185,190,185,200,180,185,185,190,192,210,219,190,185,195,190,190,210,213,190,185,209,195,200,180,180,195,190,178,190,190,200,172,185,185,180,180,170,195,175,215,195,190,185,205,195,190,220,177,170,197,175,214,180,180,180,185,190,185,185,188,205,190,165,184,210,210,190,158,203,205,185,180,175,185,175,185,175,180,204,190,207,180,200,170,190,170,200,165,184,185,185,180,170,185,165,175,170,180,190,190,193,175,165,180,200,200,185,185,191,201,180,204,220,180,175,183,185,180,190,208,185,170,185,188,189,198,175,195,175,200,195,220,180,215,170,160,175,190,190,195,175,180,170,175,170,185,180,205,185,180,205,202,220,170,218,186,200,215,200,180,185,215,180,223,188,200,175,215,190,195,180,185,170,170,195,193,190,175,165,215,185,185,178,185,185,177,180,175,170,195,206,180,175,205,170,180,210,190,153,190,185,175,175,210,180,195,185,165,185,179,150,175,180,189,173,175,210,185,210,185,195,190,175,200,205,160,180,200,190,180,210,197,215,175,180,183,175,210,185,190,178,189,195,195,180,163,170,180,195,185,200,190,190,200,193,200,180,205,185,165,205,175,170,170,175,175,200,180,209,180,195,200,180,160,209,192,184,180,175,180,199,170,190,190,195,185,205,175,195,166,175,180,165,178,190,200,185,205,214,185,203,185,175,190,200,160,175,150,205,192,180,195,190,190,197,185,180,200,165,185,200,200,170,160,195,199,190,170,185,174,189,200,170,220,180,172,175,185,175,210,190,190,178,207,180,190,175,185,185,185,180,190,190,170,200,210,180,192,190,180,190,190,205,175,180,190,190,209,160,190,195,188,185,200,170,185,210,205,185,185,175,210,191,165,185,170,175,168,195,168,180,195,180,175,200,185,210,180,150,175,211,210,190,180,170,200,185,185,185,191,175,170,190,205,190,190,175,190,195,210,180,190,185,185,175,200,165,175,180,170,190,190,165,175,185,170,207,190,145,190,175,195,175,185,170,165,210,192,200,190,190,175,208,175,179,175,200,190,175,170,190,175,175,185,170,190,170,209,185,170,160,174,180,160,175,185,175,190,210,175,185,210,180,195,160,190,165,195,190,200,180,165,180,175,195,175,219,215,190,185,185,174,175,170,195,175,200,175,185,185,185,185,180,190,165,170,220,208,185,185,220,200,150,190,195,205,190,195,175,181,180,189,175,210,205,195,180,170,195,215,215,170,175,170,183,181,165,195,170,200,190,190,185,180,170,200,170,195,185,190,205,160,185,183,185,170,185,190,190,180,175,190,220,190,188,199,180,190,185,185,195,195,170,206,195,220,200,205,190,180,223,215,215,195,175,210,195,200,170,185,180,173,185,190,195,200,185,180,180,180,195,175,170,155,185,176,190,195,168,185,175,186,190,180,165,195,180,200,195,215,155,190,194,180,185,165,215,195,180,180,195,170,175,210,195,200,210,186,175,225,185,170,195,175,205,172,185,210,180,195,210,190,190,183,175,179,190,185,180,190,169,175,190,160,190,170,200,190,170,220,190,175,168,180,205,190,184,166,202,235,170,185,175,165,185,180,190,180,205,215,205,200,175,220,180,185,190,160,194,190,200,195,160,175,190,180,170,200,185,185,165,165,200,200,208,185,170,190,225,198,185,185,170,195,175,205,190,225,185,170,180,205,175,210,208,185,165,170,180,200,171,179,201,210,175,190,160,210,180,170,200,190,170,204,175,165,160,175,185,180,175,170,190,175,210,165,185,186,189,165,195,196,185,170,190,160,208,175,175,185,180,190,185,193,200,185,211,185,195,190,205,212,175,175,185,195,178,178,185,175,150,175,200,193,160,220,195,190,175,185,204,205,183,150,185,180,205,185,183,212,185,170,173,200,195,217,190,190,202,190,185,190,195,220,160,210,200,170,185,190,225,175,190,180,184,195,172,180,195,185,215,190,163,189,160,170,165,190,195,175,190,203,195,175,195,195,190,190,190,160,175,195,185,175,200,201,170,133,165,180,175,180,208,190,180,175,210,178,200,195,177,165,185,165,180,190,195,190,195,170,195,213,160,168,155,185,195,165,185,180,185,185,180,175,215,225,165,175,180,180,190,200,180,190,212,175,190,195,175,175,205,210,175,182,198,188,175,175,188,180,201,185,185,175,175,175,175,175,190,200,195,185,160,174,164,170,185,190,185,185,180,175,195,210,210,183,185,160,205,205,180,175,180,210,205,175,205,195,170],"y":[73,75,77,72,76,77,70,73,77,77,74,76,71,73,77,74,76,75,74,77,78,74,74,78,74,77,75,77,78,72,71,72,73,73,75,75,74,77,72,75,74,74,76,74,74,71,72,70,72,72,73,74,77,77,78,75,72,78,73,73,72,76,76,78,74,75,77,72,74,73,75,73,76,75,76,70,74,71,78,77,76,78,77,76,74,70,75,74,77,75,70,77,72,73,75,77,73,72,76,78,72,75,72,71,71,73,74,75,71,73,73,73,75,75,78,75,77,78,72,76,75,76,72,73,76,72,73,74,76,76,72,76,76,78,63,76,74,77,76,78,73,77,77,73,74,65,78,73,74,71,77,75,71,73,74,74,76,76,73,76,74,76,76,77,76,72,71,74,73,72,77,75,76,72,76,79,69,77,75,75,75,74,76,77,74,72,76,73,75,78,76,75,72,74,73,77,78,73,75,75,74,75,74,76,74,74,74,75,72,73,78,75,77,73,73,70,72,72,76,69,75,77,75,76,77,75,75,78,73,77,77,77,75,77,78,77,75,76,72,74,77,76,75,73,75,72,74,75,76,77,75,74,74,76,75,76,77,76,71,75,74,78,75,74,73,76,76,74,78,71,72,72,75,74,77,73,75,73,77,76,76,74,77,75,73,74,77,75,73,78,72,72,73,73,77,73,73,74,76,77,76,72,68,70,77,76,73,73,73,75,76,72,76,75,74,75,75,75,72,76,79,76,77,73,77,70,75,75,75,74,76,77,74,75,76,78,77,74,72,77,76,73,74,78,76,75,78,73,76,75,74,74,71,75,72,73,77,76,74,72,76,75,73,73,72,75,73,78,75,75,74,72,71,74,75,77,78,75,75,74,72,74,79,67,75,75,74,73,74,79,77,73,74,74,75,73,75,75,78,75,76,74,75,75,75,63,76,76,77,70,73,76,75,71,72,75,74,70,76,77,75,76,75,76,78,75,75,72,74,72,77,73,75,78,74,77,76,76,75,73,69,78,73,72,78,72,75,74,73,73,75,77,74,75,72,74,77,76,76,75,73,75,74,72,70,76,71,73,73,72,75,74,76,77,75,77,73,76,74,74,75,76,75,72,76,76,76,75,73,78,73,76,74,75,77,72,76,74,70,74,76,75,74,74,72,79,79,74,78,74,77,77,74,74,75,77,72,77,78,74,77,73,77,73,77,75,76,75,71,75,71,73,74,76,73,78,78,75,75,67,76,75,75,73,79,76,73,72,72,74,76,76,74,76,77,73,71,76,76,75,76,75,73,75,72,75,73,78,73,77,70,74,72,73,74,75,78,76,78,72,78,77,74,73,76,76,77,76,76,74,75,75,76,78,77,77,77,77,75,78,78,73,75,77,75,77,71,77,75,75,72,76,76,75,74,74,75,72,74,77,77,74,77,76,75,75,78,79,79,78,71,75,74,70,76,74,77,72,75,76,73,76,75,78,76,66,74,79,79,74,69,76,76,78,75,72,75,75,76,70,72,79,75,79,73,78,74,75,73,75,70,77,75,76,72,74,77,72,74,73,75,76,77,75,70,72,72,75,75,73,73,75,73,72,76,78,73,75,74,75,70,74,75,75,72,75,74,73,79,73,76,71,77,77,75,73,76,73,67,71,75,75,75,70,70,72,76,73,76,74,74,73,73,75,75,77,71,77,76,74,74,77,75,75,76,75,79,76,73,73,78,74,74,74,75,71,73,76,75,75,74,70,77,71,72,74,71,76,70,73,74,72,75,78,71,75,76,73,75,76,76,71,76,73,72,74,77,74,74,76,72,78,77,67,75,72,75,70,73,76,73,78,79,72,73,76,77,75,71,74,78,74,73,76,75,76,75,76,76,71,74,78,78,73,77,75,71,73,72,73,74,79,72,77,75,75,77,76,76,72,76,75,71,76,74,75,75,75,72,78,74,78,76,75,75,72,72,76,79,74,72,74,74,77,73,76,75,72,75,72,75,73,71,72,74,72,73,73,77,74,73,76,75,75,77,75,76,76,73,75,69,76,75,74,70,79,75,77,72,74,77,71,75,75,76,71,68,77,79,75,70,74,70,72,77,73,77,76,73,75,74,75,77,74,75,74,76,71,75,75,73,79,78,73,74,75,70,74,79,76,77,76,76,75,73,76,75,72,76,75,77,72,76,77,74,73,75,73,75,76,75,78,75,77,76,75,73,74,69,72,72,74,72,74,75,72,73,75,72,77,75,67,74,75,76,76,75,72,75,75,75,79,76,73,73,74,80,77,76,75,74,76,77,75,75,74,77,75,77,72,73,74,71,73,77,69,73,77,77,76,76,69,72,73,75,71,75,75,77,76,75,76,72,75,74,75,72,73,73,76,75,73,74,76,75,73,73,74,77,74,76,74,73,69,72,73,71,73,74,74,75,76,75,74,76,71,76,71,75,74,74,75,76,74,72,74,73,75,73,74,78,76,74,76,72,74,73,73,74,76,72,74,74,75,76,76,75,73,73,79,76,75,74,77,74,72,75,78,77,76,77,73,76,76,75,76,77,76,79,77,72,75,77,76,75,71,74,75,74,73,75,72,75,74,78,75,75,76,73,73,78,74,76,75,72,74,75,74,73,73,76,74,73,74,75,78,76,78,75,74,77,75,74,73,76,73,78,75,78,78,78,77,73,78,77,77,76,74,79,75,76,72,76,74,73,75,77,76,77,73,74,69,76,74,74,75,69,72,75,73,72,72,74,73,73,75,77,70,78,70,77,77,78,70,74,76,74,73,70,78,77,75,74,77,72,70,79,76,78,79,74,74,78,76,73,75,72,75,73,75,78,70,75,77,80,75,74,73,74,75,77,71,75,72,73,78,70,75,74,74,74,74,77,78,74,73,73,77,75,73,77,75,76,73,72,77,70,72,73,75,71,77,80,75,76,73,76,73,73,76,73,76,75,74,75,72,72,74,75,75,75,74,76,71,72,76,79,74,75,74,75,78,75,75,73,68,76,74,77,77,74,75,77,75,78,74,77,77,74,71,73,73,78,70,73,77,75,75,76,72,77,73,74,77,75,74,75,70,69,72,76,74,78,72,75,75,76,76,74,75,74,74,72,78,77,74,73,79,73,76,76,75,69,73,75,74,76,74,73,78,76,76,76,76,77,74,72,72,75,75,74,73,73,67,75,76,77,71,79,74,74,73,73,78,75,77,70,76,74,75,73,73,78,75,73,73,77,72,78,74,73,78,73,74,76,79,76,71,77,74,72,77,74,76,75,76,76,72,75,73,75,76,73,76,76,71,73,72,72,74,74,76,70,77,76,77,71,74,76,76,74,76,72,74,73,75,73,74,78,76,66,74,74,74,73,79,72,76,74,77,76,75,76,75,72,73,70,73,77,74,75,74,74,75,76,70,72,69,76,77,74,76,73,70,77,73,75,78,77,72,74,75,75,74,75,74,77,75,74,73,74,74,73,75,77,74,74,73,75,73,74,75,75,73,74,76,75,75,74,70,76,72,77,75,77,73,74,73,74,74,76,75,70,74,69,77,75,73,77,75,73,74,78,74,75,74,77,81,73,75,75,73],"z":[2001,1957,2009,1954,2009,2016,1996,1975,2018,2011,2012,1995,2013,2005,2003,1991,1997,2018,1979,2014,2012,2010,1970,2010,1976,2008,1983,1977,2018,2005,1989,2002,2016,1984,2018,2012,2000,2004,2008,1979,1966,2011,1970,1954,1958,2010,1971,1947,2018,1968,1978,2002,2012,2014,2018,1973,1994,2000,1999,2005,1947,2018,2017,2018,2011,2017,1996,2018,1952,2002,1976,1972,1977,1977,1971,2008,1973,2004,2009,2000,2006,2018,2006,1983,1995,1947,2018,1995,2018,1979,1951,2018,2013,1999,2011,2012,2004,1961,1976,2003,1997,1969,1995,1980,2005,2018,1968,1966,1947,1981,2012,1969,2014,1978,2018,1989,1981,1994,1995,1988,2016,2018,2007,1962,1993,2002,2018,1951,2018,1982,1953,2005,1965,2018,2001,1958,1978,1995,1997,2018,1997,2002,1997,1979,1978,2012,2007,1975,2018,1968,1984,1950,2002,1953,1986,2004,2005,1986,1956,1968,1978,1981,1983,2018,1978,2018,1998,2018,2002,2009,2010,1984,1999,1947,2015,2005,1972,2018,2000,2016,1992,2003,2015,2018,2005,1973,2006,1972,1976,1990,2009,1986,1953,1978,2017,1982,2018,2006,2006,1950,1982,1968,1993,1985,1966,1965,1972,2015,2015,1952,2015,2018,2018,1992,1947,1949,1981,2018,1974,1962,2005,1990,1955,1981,2001,1999,1973,2013,2012,1986,1985,2004,1982,1980,2018,2018,2008,2000,2005,2018,1980,2000,1978,1993,1981,2015,1997,2003,1955,2014,2017,1970,1976,1985,2018,1969,2018,2018,2009,1980,2006,2018,1987,2017,2004,1981,1998,1972,2010,2011,2018,2001,1995,1975,1964,1972,1968,2018,2018,1976,1995,2013,2013,1989,2005,2018,2018,1971,1994,1992,1994,1953,1968,2016,1999,1965,1970,1983,1963,2018,2018,2002,1985,1969,2009,1980,1950,2003,1968,2002,2016,1950,2002,2010,2017,2018,1977,1992,1979,2011,1998,2018,1997,1950,1975,1962,1971,2012,1992,1974,2003,2004,1986,1973,1962,2010,2015,1995,1968,2014,1980,1971,1999,2016,2002,2018,2013,2006,2018,1997,1959,1953,2013,1973,1976,1967,1958,2004,2008,2008,1977,1975,1952,2010,1978,1982,1991,2018,1955,2009,1997,1951,1988,1950,2013,2018,2018,2009,1987,1983,2001,2017,2015,1972,2011,2018,2004,1991,2015,1998,1997,1958,1979,1983,1965,2013,1999,1969,1998,1990,2018,1958,1983,1976,2012,1969,1987,1958,1984,2001,1988,1990,2001,1972,1949,1962,2006,2001,2018,1998,2017,1977,1992,1995,2013,2018,1996,1970,1950,2018,2012,1988,2007,2017,2017,2009,1994,1977,1956,1953,2018,2014,2018,1953,2012,2018,1972,1975,1955,2014,2006,1996,2005,1995,2012,1978,1976,2002,1971,2018,1995,1972,1985,2012,1949,2003,2012,1976,1986,1970,2018,1973,2017,2008,2008,2015,2018,1980,2016,1988,1976,1969,1975,1948,1981,2018,1969,1995,1968,2006,2012,1982,2018,2005,2009,1949,1980,1995,2001,1999,2014,1974,1992,2000,1950,1999,2017,1998,2017,1961,1995,2018,2013,2017,1964,2010,2009,2005,2018,1987,2005,2006,1989,1979,2017,2015,2018,1988,1948,2016,1954,1994,1968,1998,1969,2011,2018,1987,2001,1996,2018,1985,1999,1968,2006,2016,1999,1992,2008,1979,2015,2011,2007,1991,1955,1947,1953,1965,1970,2006,1970,2016,2003,1991,1982,1971,1970,2010,1968,1973,1976,1981,1968,1948,1955,2013,1992,1978,2004,2003,2018,2018,1969,1969,1995,1999,2003,2007,1972,1975,1956,2018,2018,2018,2005,2017,1990,2013,1995,2017,2018,1958,2010,2018,1976,2010,1951,1983,1962,2001,2001,1979,1976,1971,1949,1974,2011,2004,1970,1955,1988,1992,2017,1988,1983,1957,1986,1988,1994,2015,1999,1950,2001,1951,2018,1975,2013,1982,1984,1984,1962,1965,2018,2018,2016,1947,2007,2012,2007,1992,1948,2005,2018,2018,1982,1979,1985,1968,1990,1954,1969,2014,2000,2018,2011,2005,1977,2015,2008,2017,1990,2012,1995,1963,1992,2010,2017,1998,1987,1952,1976,1969,1993,2018,1993,2010,1969,2014,2018,1968,2009,2010,2018,1975,2006,2006,2004,1973,1990,1987,2017,1985,2018,1994,1981,1974,2014,2018,2009,1969,2007,1950,2014,2009,2013,2005,2017,2017,1995,2011,1970,2010,2012,2004,2012,1979,1984,1996,1990,1987,1990,1994,2000,1978,2015,2016,1953,2012,2018,1992,2014,1995,2000,2009,2013,1972,2018,1977,1967,1984,2005,1973,2018,1976,1965,1999,1984,2000,2018,1976,1949,1947,2010,1947,1950,1955,1959,1986,1976,1947,1972,1949,1974,2018,1961,2003,2013,1953,1971,2018,1993,1993,1981,1997,1958,1973,1997,1973,1963,1974,1947,2009,2005,1948,1951,2005,2017,2009,1999,1993,1974,1965,2018,1949,1949,1981,1970,1977,1950,1980,2005,2010,1977,2014,2002,2008,1976,2017,1962,2018,2004,1977,1978,1971,2017,2011,2017,1978,1957,1989,1990,2015,1980,2018,1976,1991,2015,1982,2000,1974,2006,1963,1995,2012,1986,1991,1994,1971,1977,1990,1968,2018,1975,2018,2018,1970,1975,2007,2018,1969,1970,1951,1971,2002,2005,1995,1973,1990,1972,2018,1990,2015,2017,2009,1954,1976,1953,1968,2017,1955,2013,2006,1982,2018,1999,1987,2003,1998,2018,1973,1949,1996,2003,1974,1947,1989,1963,1980,1947,2009,1997,1948,1973,1978,2016,2008,1948,1991,2016,1955,1960,1962,1954,2018,2014,1990,2018,2001,1999,1992,1976,2014,2016,1993,2016,1960,2009,1950,1981,1972,1964,2018,1986,1979,1953,2018,1953,2018,1981,1977,2007,1982,1996,1982,1949,2017,1974,1960,2008,1970,2007,1986,1992,2018,2007,1960,2015,1962,1955,2001,1975,2017,1966,1995,2018,2015,1976,1975,1947,1977,1957,1981,1950,1963,1968,1947,2006,2016,2018,1996,1988,1948,2000,2018,1968,2009,1991,1980,2018,1980,1992,2016,2018,1990,1983,1968,1983,1972,2015,2018,1968,1990,2017,1992,1989,1987,1998,1975,2018,1950,1947,2016,1948,2000,1977,1983,1947,2013,2018,2018,2010,1949,1950,2018,2014,1996,1985,2008,1991,2017,2014,2009,2018,1978,1971,1997,1971,2018,1967,1993,1997,1983,1989,1962,1979,2006,1949,1968,2018,1987,2018,1953,1975,1953,1950,1950,1949,1971,1951,1953,1970,2018,1951,1977,1998,2003,2010,1950,1970,1993,1953,2004,2008,2004,1975,1972,2018,2006,2015,2013,2012,2008,2018,1976,1950,1950,1949,1947,1958,2018,2018,1958,1994,2017,2018,2007,2018,1947,1947,1980,2005,2002,1974,2005,2018,2002,1970,2005,1970,1976,1993,1954,1995,1988,1966,1973,2000,1998,2006,1987,1983,2002,2003,2018,1969,2016,1989,1973,2015,2002,1979,1998,1973,2017,1981,2016,1996,2009,2018,1950,2017,2013,1983,1979,1953,1953,2003,2017,1986,1952,2011,2007,1960,1969,2002,2012,2018,1980,2000,1958,1981,1996,1952,1999,1970,1953,2015,1987,2015,2018,2018,2002,1999,2013,2002,2002,1972,2015,2003,1974,2018,1992,1996,2009,2017,1996,2000,1979,1998,1974,2001,2016,1983,1997,1974,1982,1948,1970,2017,1977,1964,1953,1961,1985,2018,2018,1989,1947,2011,1948,1987,1986,2013,1950,2018,2018,1993,1996,1950,2010,2018,1973,1968,1988,2012,1951,2015,2003,2003,2018,2003,1969,2003,2006,1973,1957,1947,1968,2018,1968,1987,1955,1997,1998,2000,1950,2013,1970,1954,2018,1985,1947,2014,1998,1961,2003,1975,1999,1983,1990,1949,1964,2018,2015,1974,1990,1982,2012,1969,1947,2018,1999,1999,1978,2009,1987,1954,2014,1996,1980,1957,1983,2005,2016,1985,1989,2018,1972,1976,1962,1996,2006,1995,2014,2018,1975,2018,2012,1987,1997,1994,2013,1983,1985,2016,1980,2005,1997,2001,1980,2008,2008,1986,1960,2009,1969,2007,1992,1957,2005,1949,1982,1987,2002,2018,1991,2013,2002,1962,2015,2003,1947,2018,2008,2008,2008,2005,2005,1993,1968,2017,1955,1992,2005,1985,1996,1974,1947,2005,1949,1989,1982,2007,1977,2018,1990,1987,2011,2009,2014,2018,2014,2015,2018,2018,2018,1970,1991,1974,2008,1998,1992,2017,1994,1991,1968,1998,1975,1969,2012,1992,1971,1970,2017,2018,1997,1948,1963,2014,1988,1994,1949,1954,1977,1982,2004,1993,1992,2018,1968,2000,1980,1995,2012,2017,2010,2018,1954,1991,2012,1970,1991,2018,1972,2006,1979,2001,2018,2017,1970,2009,2018,1974,1992,2000,2017,2018,1990,2012,2007,1950,1991,1969,2018,1980,1977,1993,1984,1976,2018,1978,2018,1947,1988,2000,1954,2018,1981,1957,1975,2005,1967,2014,1976,2011,1986,1972,2008,1993,1999,1989,1975,1955,2017,2014,1971,1979,2014,2011,1972,1998,2018,1977,1968,1963,2006,2007,2012,1974,2011,1968,2018,1984,1997,1999,1989,1999,1955,2018,1971,1981,1981,1988,1986,2018,1998,2004,1950,1992,2017,1950,1995,1975,2010,2007,1975,1974,2003,2018,1973,1978,1977,1969,1994,2017,1980,2016,2005,1987,2011,2003,1989,2018,2010,2018,1999,1975,2016,1987,1983,1984,1976,1970,2007,1981,1952,1978,1980,1973,1971,1987,1987,1980,1988,1972,1960,1976,1972,1976,1978,2018,1991,1996,2000,1969,1982,2007,2013,2018,1972,1982,1972,2016,1991,1995,2018,1987,2009,1962,1972,2006,1971],"type":"scatter3d","mode":"markers","name":"G","marker":{"color":"rgba(255,217,47,1)","line":{"color":"rgba(255,217,47,1)"}},"textfont":{"color":"rgba(255,217,47,1)"},"error_y":{"color":"rgba(255,217,47,1)"},"error_x":{"color":"rgba(255,217,47,1)"},"line":{"color":"rgba(255,217,47,1)"},"frame":null},{"x":[190,213,220,200,213,190,170,213,210,197,185,190,170,180,185,201,190,190,185,210,175,215,216,200,190,185,195,180,220,220,200,195,212,189,205,218,210,210,170,195,185,220,170,190,209,210,200,209,195,180,180,210,185,155,170,210,210,215,189,214,200,175,175,210,198,193,188,221,225,190,190,200,192,220,218,200,180,210,205,220,190,203,184,190,215,190,189,190,205,185,190,170,210,200,210,220,180,190,210,221,205,175,215,205,210,185,175,210,217,210,175,230,170,199,180,195,220,188,185,205,185,195,180,185,220,195,180,205,185,195,205,206,200,215,200,190,200,205,215,215,190,225,225,210,240,215,195,225,190,210,180,198,205,195,185,185,170,208,180,187,173,195,185,212,200,193,210,230,200,210,185,185,200,185,203,195,205,205,195,195,180,215,200,190,190,213,190,200,205,205,190,205,180,185,195,195,185,210,225,195,235,190,185,225,185,210,200,190,190,195,180,185,200,200,165,209,185,195,205,185,205,225,220,200,174,190,185,185,205,195,215,200,215,220,195,185,204,190,165,205,175,165,200,225,185,189,180,205,200,185,210,205,210,210,222,185,195,210,220,214,210,185,175,175,220,196,230,165,180,190,180,170,175,200,230,210,195,200,220,195,195,190,205,190,215,225,210,180,200,207,180,190,218,190,180,188,185,230,195,195,222,170,195,185,180,194,180,210,195,170,195,195,206,215,210,210,185,197,170,190,200,200,210,185,195,170,205,160,195,200,180,230,205,210,200,190,205,200,235,185,195,185,200,190,180,210,185,185,210,190,193,195,210,210,190,215,210,170,215,195],"y":[78,76,78,74,78,79,71,79,78,79,77,76,76,75,76,77,77,76,73,77,71,77,80,74,78,78,78,77,79,78,77,79,78,77,79,79,77,77,72,78,75,78,71,78,79,80,78,77,78,74,78,78,75,70,77,78,78,78,76,77,78,73,74,79,78,78,78,79,79,77,74,77,76,77,79,76,78,77,79,78,76,79,79,76,79,74,75,77,79,76,76,71,78,75,76,80,79,75,78,77,78,73,78,79,77,74,74,77,77,78,77,78,73,77,72,79,79,73,78,79,79,79,74,78,79,78,71,81,75,74,77,80,77,78,74,76,80,78,78,76,77,79,80,79,79,81,78,78,78,76,74,76,77,78,74,78,74,79,72,74,75,78,74,79,77,74,76,77,77,77,77,74,77,77,79,79,76,78,77,77,72,78,78,78,81,77,75,79,78,78,77,77,74,75,77,77,74,79,78,76,78,76,79,78,74,78,76,76,74,77,78,74,78,76,73,77,74,73,77,75,74,77,80,78,76,75,76,75,78,74,79,77,78,79,76,77,77,73,74,76,75,71,80,78,78,77,71,76,76,74,79,77,78,80,78,75,76,80,78,81,77,74,72,77,79,75,77,70,75,74,73,71,74,73,82,79,78,77,77,77,73,77,78,74,79,78,77,75,79,77,72,77,78,78,77,77,75,77,77,77,78,70,74,77,77,74,77,77,76,74,76,79,80,79,78,78,72,79,72,77,79,77,77,75,75,73,78,74,76,77,75,79,78,77,78,77,76,79,77,74,78,78,77,76,75,77,77,76,78,79,78,77,79,79,74,78,79,74,80,75],"z":[2018,2018,2017,1971,2016,1997,1951,2018,1998,1999,1980,1974,1977,1956,1975,2018,1971,1961,1947,2018,1950,2014,2018,1981,1998,1981,1989,1962,2014,2018,2014,2018,2016,2005,2018,2001,2004,1969,1951,1980,1977,2018,1953,1972,2006,2014,2007,2015,1996,1950,1981,2018,1955,1950,1990,2001,2018,2018,1971,1995,2013,1955,1947,2000,1982,1992,2001,2018,2010,2003,1954,2015,1991,1998,2017,1999,1997,2001,2000,2018,1959,2004,2018,1963,2010,1953,1960,1982,2018,1958,1980,1955,2017,1961,1951,2010,1986,1977,2008,1996,1966,1948,2018,2017,1994,1966,1973,1985,2008,1986,1976,2016,1951,1973,1950,2018,2016,1949,2013,1997,1990,2008,1951,2001,2003,1982,1948,1998,1973,1955,2018,2018,1992,2018,1975,2002,2018,1984,2008,2001,1994,2014,2004,1994,2018,1996,1990,2017,2008,2009,1974,1969,1976,2003,1949,1983,1948,2016,1947,1960,1952,1985,1955,2018,1970,1953,1968,1969,1974,1963,2018,1950,1995,1975,2018,1993,1994,1990,1997,1993,1951,2002,2016,1994,2007,1997,1955,1999,2002,2017,1990,1976,1955,1970,1988,1998,1949,2005,2018,1972,1999,1975,2005,2017,1953,1999,1997,1976,1955,2015,1998,1949,1978,1982,1950,1999,1951,1947,1999,1952,1960,2017,2013,1990,1953,1951,1970,1969,1984,1958,2008,1981,2013,2018,1972,1993,2006,1949,1949,1970,1954,1950,1996,2000,2009,1986,1949,1976,1977,1951,2018,1974,2007,2004,2017,1969,1955,2007,2017,2018,2006,1955,1950,1980,2018,1950,2018,1950,1964,1950,1960,1949,1950,1950,2018,2012,2018,1980,1968,1976,1952,1962,1991,1949,2006,2018,1992,1983,2018,1979,1950,1984,2013,1977,1980,2014,1956,2018,1989,1993,2008,1949,1971,1980,1972,1974,1983,1983,1978,1971,1984,2007,2017,2018,1986,1996,1950,2017,1950,1989,1995,1962,1977,1950,1952,1950,2006,1955,1977,1970,1974,2015,2016,2008,2001,1976,1971,2013,1982,1961,1983,1999,1975,1986,2000,1993,2001,1983,1992,1982,1987,1991,2011,2003,1972,2017,2018,1956,2018,1949],"type":"scatter3d","mode":"markers","name":"G-F","marker":{"color":"rgba(229,196,148,1)","line":{"color":"rgba(229,196,148,1)"}},"textfont":{"color":"rgba(229,196,148,1)"},"error_y":{"color":"rgba(229,196,148,1)"},"error_x":{"color":"rgba(229,196,148,1)"},"line":{"color":"rgba(229,196,148,1)"},"frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.20000000000000001,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>
</div>
</div>
<p>Not a big fan of the 3D plot. Too much going on. Thinking about using a ratio of height to weight instead of both variables.</p>
</section>
<section id="go-to-this-website-and-use-one-of-the-50-best-plots-to-visualize-some-aspect-of-the-data-and-provide-at-least-one-insight.-you-will-present-your-work-in-breakout-httpr-statistics.cotop50-ggplot2-visualizations-masterlist-r-code.html" class="level4">
<h4 class="anchored" data-anchor-id="go-to-this-website-and-use-one-of-the-50-best-plots-to-visualize-some-aspect-of-the-data-and-provide-at-least-one-insight.-you-will-present-your-work-in-breakout-httpr-statistics.cotop50-ggplot2-visualizations-masterlist-r-code.html">Go to this website and use one of the 50 best plots to visualize some aspect of the data and provide at least one insight. You will present your work in breakout! http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html</h4>
<p>I have decided to quit my job and be a full time QUILT MAKER!</p>
<div class="cell">
<div class="code-copy-outer-scaffold"><div class="sourceCode cell-code" id="cb26"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb26-1"><a href="#cb26-1" aria-hidden="true" tabindex="-1"></a><span class="co"># Now we'll need to clean and process some data for a quilt plot.</span></span>
<span id="cb26-2"><a href="#cb26-2" aria-hidden="true" tabindex="-1"></a><span class="co"># Need to simplify positions for my first quilt.</span></span>
<span id="cb26-3"><a href="#cb26-3" aria-hidden="true" tabindex="-1"></a>player_data <span class="ot">&lt;-</span> player_data <span class="sc">%&gt;%</span></span>
<span id="cb26-4"><a href="#cb26-4" aria-hidden="true" tabindex="-1"></a>  <span class="fu">mutate</span>(</span>
<span id="cb26-5"><a href="#cb26-5" aria-hidden="true" tabindex="-1"></a>    <span class="co"># Simplify positions (e.g., "F-C" -&gt; "F", keep main ones: C, F, G)</span></span>
<span id="cb26-6"><a href="#cb26-6" aria-hidden="true" tabindex="-1"></a>    <span class="at">position_simple =</span> <span class="fu">str_extract</span>(position, <span class="st">"^[CFG]"</span>),  <span class="co"># Extract first letter: C, F, G</span></span>
<span id="cb26-7"><a href="#cb26-7" aria-hidden="true" tabindex="-1"></a>    <span class="co"># Create decade from year_start</span></span>
<span id="cb26-8"><a href="#cb26-8" aria-hidden="true" tabindex="-1"></a>    <span class="at">decade =</span> <span class="fu">floor</span>(year_start <span class="sc">/</span> <span class="dv">10</span>) <span class="sc">*</span> <span class="dv">10</span></span>
<span id="cb26-9"><a href="#cb26-9" aria-hidden="true" tabindex="-1"></a>  ) <span class="sc">%&gt;%</span></span>
<span id="cb26-10"><a href="#cb26-10" aria-hidden="true" tabindex="-1"></a>  <span class="fu">filter</span>(<span class="sc">!</span><span class="fu">is.na</span>(position_simple), <span class="sc">!</span><span class="fu">is.na</span>(decade), <span class="sc">!</span><span class="fu">is.na</span>(height_inches), <span class="sc">!</span><span class="fu">is.na</span>(weight))  <span class="co"># Drop invalid</span></span>
<span id="cb26-11"><a href="#cb26-11" aria-hidden="true" tabindex="-1"></a></span>
<span id="cb26-12"><a href="#cb26-12" aria-hidden="true" tabindex="-1"></a><span class="co"># Need to gather my textures (data) for the quilt. Copilot need to help me group and order.</span></span>
<span id="cb26-13"><a href="#cb26-13" aria-hidden="true" tabindex="-1"></a><span class="co"># Summarize: Count players per position per decade</span></span>
<span id="cb26-14"><a href="#cb26-14" aria-hidden="true" tabindex="-1"></a>quilt_summary <span class="ot">&lt;-</span> player_data <span class="sc">%&gt;%</span></span>
<span id="cb26-15"><a href="#cb26-15" aria-hidden="true" tabindex="-1"></a>  <span class="fu">group_by</span>(decade, position_simple) <span class="sc">%&gt;%</span></span>
<span id="cb26-16"><a href="#cb26-16" aria-hidden="true" tabindex="-1"></a>  <span class="fu">summarise</span>(<span class="at">count =</span> <span class="fu">n</span>(), <span class="at">.groups =</span> <span class="st">"drop"</span>) <span class="sc">%&gt;%</span></span>
<span id="cb26-17"><a href="#cb26-17" aria-hidden="true" tabindex="-1"></a>  <span class="co"># For each decade, rank positions by count (descending)</span></span>
<span id="cb26-18"><a href="#cb26-18" aria-hidden="true" tabindex="-1"></a>  <span class="fu">group_by</span>(decade) <span class="sc">%&gt;%</span></span>
<span id="cb26-19"><a href="#cb26-19" aria-hidden="true" tabindex="-1"></a>  <span class="fu">arrange</span>(decade, <span class="fu">desc</span>(count)) <span class="sc">%&gt;%</span> <span class="co"># change to asc(mean_height) for height based ranking</span></span>
<span id="cb26-20"><a href="#cb26-20" aria-hidden="true" tabindex="-1"></a>  <span class="fu">mutate</span>(<span class="at">rank =</span> <span class="fu">row_number</span>()) <span class="sc">%&gt;%</span> </span>
<span id="cb26-21"><a href="#cb26-21" aria-hidden="true" tabindex="-1"></a>  <span class="fu">ungroup</span>()</span>
<span id="cb26-22"><a href="#cb26-22" aria-hidden="true" tabindex="-1"></a></span>
<span id="cb26-23"><a href="#cb26-23" aria-hidden="true" tabindex="-1"></a><span class="co"># Now to pickout my colors for the quilt.</span></span>
<span id="cb26-24"><a href="#cb26-24" aria-hidden="true" tabindex="-1"></a>positions <span class="ot">&lt;-</span> <span class="fu">unique</span>(quilt_summary<span class="sc">$</span>position_simple)</span>
<span id="cb26-25"><a href="#cb26-25" aria-hidden="true" tabindex="-1"></a>position_colors <span class="ot">&lt;-</span> <span class="fu">setNames</span>(<span class="fu">rainbow</span>(<span class="fu">length</span>(positions)), positions)  <span class="co"># Or use scale_fill_manual with custom colors</span></span>
<span id="cb26-26"><a href="#cb26-26" aria-hidden="true" tabindex="-1"></a></span>
<span id="cb26-27"><a href="#cb26-27" aria-hidden="true" tabindex="-1"></a><span class="co"># Now to start sewing! </span></span>
<span id="cb26-28"><a href="#cb26-28" aria-hidden="true" tabindex="-1"></a><span class="fu">ggplot</span>(quilt_summary, <span class="fu">aes</span>(<span class="at">x =</span> <span class="fu">as.factor</span>(decade), <span class="at">y =</span> <span class="sc">-</span>rank, <span class="at">fill =</span> position_simple)) <span class="sc">+</span>  <span class="co"># y = -rank to have best (rank 1) at top</span></span>
<span id="cb26-29"><a href="#cb26-29" aria-hidden="true" tabindex="-1"></a>  <span class="fu">geom_tile</span>(<span class="at">color =</span> <span class="st">"white"</span>, <span class="at">linewidth =</span> <span class="fl">0.5</span>) <span class="sc">+</span>  <span class="co"># Tiles for background color</span></span>
<span id="cb26-30"><a href="#cb26-30" aria-hidden="true" tabindex="-1"></a>  <span class="fu">geom_text</span>(<span class="fu">aes</span>(<span class="at">label =</span> <span class="fu">paste</span>(position_simple, <span class="st">"</span><span class="sc">\n</span><span class="st">"</span>, count)), <span class="at">color =</span> <span class="st">"black"</span>, <span class="at">size =</span> <span class="dv">3</span>) <span class="sc">+</span>  <span class="co"># Text: Position + count</span></span>
<span id="cb26-31"><a href="#cb26-31" aria-hidden="true" tabindex="-1"></a>  <span class="fu">scale_fill_manual</span>(<span class="at">values =</span> position_colors) <span class="sc">+</span>  <span class="co"># Unique colors per position</span></span>
<span id="cb26-32"><a href="#cb26-32" aria-hidden="true" tabindex="-1"></a>  <span class="fu">scale_y_continuous</span>(<span class="at">breaks =</span> <span class="sc">-</span><span class="fu">max</span>(quilt_summary<span class="sc">$</span>rank)<span class="sc">:</span> <span class="sc">-</span><span class="dv">1</span>, <span class="at">labels =</span> <span class="fu">max</span>(quilt_summary<span class="sc">$</span>rank)<span class="sc">:</span><span class="dv">1</span>) <span class="sc">+</span>  <span class="co"># Reverse y for top=best</span></span>
<span id="cb26-33"><a href="#cb26-33" aria-hidden="true" tabindex="-1"></a>  <span class="fu">labs</span>(</span>
<span id="cb26-34"><a href="#cb26-34" aria-hidden="true" tabindex="-1"></a>    <span class="at">title =</span> <span class="st">"NBA Positions Quilt"</span>,</span>
<span id="cb26-35"><a href="#cb26-35" aria-hidden="true" tabindex="-1"></a>    <span class="at">subtitle =</span> <span class="st">"Inspired by finance performance quilts"</span>,</span>
<span id="cb26-36"><a href="#cb26-36" aria-hidden="true" tabindex="-1"></a>    <span class="at">x =</span> <span class="st">"Decade (based on year_start)"</span>,</span>
<span id="cb26-37"><a href="#cb26-37" aria-hidden="true" tabindex="-1"></a>    <span class="at">y =</span> <span class="st">"Rank (Most Players at Top)"</span>,</span>
<span id="cb26-38"><a href="#cb26-38" aria-hidden="true" tabindex="-1"></a>    <span class="at">fill =</span> <span class="st">"Position"</span></span>
<span id="cb26-39"><a href="#cb26-39" aria-hidden="true" tabindex="-1"></a>  ) <span class="sc">+</span></span>
<span id="cb26-40"><a href="#cb26-40" aria-hidden="true" tabindex="-1"></a>  <span class="fu">theme_minimal</span>() <span class="sc">+</span></span>
<span id="cb26-41"><a href="#cb26-41" aria-hidden="true" tabindex="-1"></a>  <span class="fu">theme</span>(</span>
<span id="cb26-42"><a href="#cb26-42" aria-hidden="true" tabindex="-1"></a>    <span class="at">panel.grid =</span> <span class="fu">element_blank</span>(),</span>
<span id="cb26-43"><a href="#cb26-43" aria-hidden="true" tabindex="-1"></a>    <span class="at">axis.text.y =</span> <span class="fu">element_text</span>(<span class="at">size =</span> <span class="dv">10</span>)</span>
<span id="cb26-44"><a href="#cb26-44" aria-hidden="true" tabindex="-1"></a>  )</span></code></pre></div><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></div>
<div class="cell-output-display">
<div>
<figure class="figure">
<p><img src="Aaron_Powell_ForLiveSession_Unit2_files/figure-html/NBA%20Quilt%20take%201-1.png" class="img-fluid figure-img" width="672"></p>
</figure>
</div>
</div>
</div>
<div class="cell">
<div class="code-copy-outer-scaffold"><div class="sourceCode cell-code" id="cb27"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb27-1"><a href="#cb27-1" aria-hidden="true" tabindex="-1"></a><span class="co"># Now we'll need to clean and process some data for a quilt plot.</span></span>
<span id="cb27-2"><a href="#cb27-2" aria-hidden="true" tabindex="-1"></a><span class="co"># Need to simplify positions for my first quilt.</span></span>
<span id="cb27-3"><a href="#cb27-3" aria-hidden="true" tabindex="-1"></a>player_data <span class="ot">&lt;-</span> player_data <span class="sc">%&gt;%</span></span>
<span id="cb27-4"><a href="#cb27-4" aria-hidden="true" tabindex="-1"></a>  <span class="fu">mutate</span>(</span>
<span id="cb27-5"><a href="#cb27-5" aria-hidden="true" tabindex="-1"></a>    <span class="co"># Simplify positions (e.g., "F-C" -&gt; "F", keep main ones: C, F, G)</span></span>
<span id="cb27-6"><a href="#cb27-6" aria-hidden="true" tabindex="-1"></a>    <span class="co">#position_simple = str_extract(position, "^[CFG]"),  # Extract first letter: C, F, G</span></span>
<span id="cb27-7"><a href="#cb27-7" aria-hidden="true" tabindex="-1"></a>    <span class="co"># Create decade from year_start</span></span>
<span id="cb27-8"><a href="#cb27-8" aria-hidden="true" tabindex="-1"></a>    <span class="at">decade =</span> <span class="fu">floor</span>(year_end <span class="sc">/</span> <span class="dv">10</span>) <span class="sc">*</span> <span class="dv">10</span></span>
<span id="cb27-9"><a href="#cb27-9" aria-hidden="true" tabindex="-1"></a>  ) <span class="sc">%&gt;%</span></span>
<span id="cb27-10"><a href="#cb27-10" aria-hidden="true" tabindex="-1"></a>  <span class="fu">filter</span>(<span class="sc">!</span><span class="fu">is.na</span>(position), <span class="sc">!</span><span class="fu">is.na</span>(decade), <span class="sc">!</span><span class="fu">is.na</span>(height_inches), <span class="sc">!</span><span class="fu">is.na</span>(weight))  <span class="co"># Drop invalid</span></span>
<span id="cb27-11"><a href="#cb27-11" aria-hidden="true" tabindex="-1"></a></span>
<span id="cb27-12"><a href="#cb27-12" aria-hidden="true" tabindex="-1"></a><span class="co"># Need to see what textures (data) I have for the quilt. Copilot need to help me group and order.</span></span>
<span id="cb27-13"><a href="#cb27-13" aria-hidden="true" tabindex="-1"></a><span class="co"># Summarize: Count players per position per decade</span></span>
<span id="cb27-14"><a href="#cb27-14" aria-hidden="true" tabindex="-1"></a>quilt_summary <span class="ot">&lt;-</span> player_data <span class="sc">%&gt;%</span></span>
<span id="cb27-15"><a href="#cb27-15" aria-hidden="true" tabindex="-1"></a>  <span class="fu">group_by</span>(decade, position) <span class="sc">%&gt;%</span></span>
<span id="cb27-16"><a href="#cb27-16" aria-hidden="true" tabindex="-1"></a>  <span class="fu">summarise</span>(</span>
<span id="cb27-17"><a href="#cb27-17" aria-hidden="true" tabindex="-1"></a>    <span class="at">mean_height =</span> <span class="fu">mean</span>(height_inches, <span class="at">na.rm =</span> <span class="cn">TRUE</span>),</span>
<span id="cb27-18"><a href="#cb27-18" aria-hidden="true" tabindex="-1"></a>    <span class="at">mean_weight =</span> <span class="fu">mean</span>(weight, <span class="at">na.rm =</span> <span class="cn">TRUE</span>),</span>
<span id="cb27-19"><a href="#cb27-19" aria-hidden="true" tabindex="-1"></a>    <span class="at">count =</span> <span class="fu">n</span>(), <span class="at">.groups =</span> <span class="st">"drop"</span>) <span class="sc">%&gt;%</span></span>
<span id="cb27-20"><a href="#cb27-20" aria-hidden="true" tabindex="-1"></a>  <span class="co"># For each decade, rank positions by mean_height descending</span></span>
<span id="cb27-21"><a href="#cb27-21" aria-hidden="true" tabindex="-1"></a>  <span class="fu">group_by</span>(decade) <span class="sc">%&gt;%</span> <span class="co"># Layout all the textures I want to use.</span></span>
<span id="cb27-22"><a href="#cb27-22" aria-hidden="true" tabindex="-1"></a>  <span class="fu">arrange</span>(decade, <span class="fu">desc</span>(mean_height)) <span class="sc">%&gt;%</span> <span class="co"># change to asc(mean_height) for height based ranking</span></span>
<span id="cb27-23"><a href="#cb27-23" aria-hidden="true" tabindex="-1"></a>  <span class="fu">mutate</span>(<span class="at">rank =</span> <span class="fu">row_number</span>()) <span class="sc">%&gt;%</span> <span class="co"># maybe I can put mean weight colors here</span></span>
<span id="cb27-24"><a href="#cb27-24" aria-hidden="true" tabindex="-1"></a>  <span class="fu">ungroup</span>()</span>
<span id="cb27-25"><a href="#cb27-25" aria-hidden="true" tabindex="-1"></a></span>
<span id="cb27-26"><a href="#cb27-26" aria-hidden="true" tabindex="-1"></a><span class="co"># Pick out the threads and needles.</span></span>
<span id="cb27-27"><a href="#cb27-27" aria-hidden="true" tabindex="-1"></a><span class="co"># positions &lt;- unique(quilt_summary$position_simple)</span></span>
<span id="cb27-28"><a href="#cb27-28" aria-hidden="true" tabindex="-1"></a><span class="co"># position_colors &lt;- setNames(rainbow(length(positions)), positions)  # Or use scale_fill_manual with custom colors</span></span>
<span id="cb27-29"><a href="#cb27-29" aria-hidden="true" tabindex="-1"></a></span>
<span id="cb27-30"><a href="#cb27-30" aria-hidden="true" tabindex="-1"></a><span class="co"># Now to start sewing! </span></span>
<span id="cb27-31"><a href="#cb27-31" aria-hidden="true" tabindex="-1"></a><span class="fu">ggplot</span>(quilt_summary, <span class="fu">aes</span>(<span class="at">x =</span> <span class="fu">as.factor</span>(decade), <span class="at">y =</span> <span class="sc">-</span>rank, <span class="at">fill =</span> mean_weight)) <span class="sc">+</span>  <span class="co"># y = -rank to have best (rank 1) at top</span></span>
<span id="cb27-32"><a href="#cb27-32" aria-hidden="true" tabindex="-1"></a>  <span class="fu">geom_tile</span>(<span class="at">color =</span> <span class="st">"white"</span>, <span class="at">linewidth =</span> <span class="fl">0.5</span>) <span class="sc">+</span>  <span class="co"># Tiles for background color</span></span>
<span id="cb27-33"><a href="#cb27-33" aria-hidden="true" tabindex="-1"></a>  <span class="fu">geom_text</span>(<span class="fu">aes</span>(<span class="at">label =</span> position), <span class="at">color =</span> <span class="st">"black"</span>, <span class="at">size =</span> <span class="dv">3</span>) <span class="sc">+</span>  <span class="co"># Text: Position + count</span></span>
<span id="cb27-34"><a href="#cb27-34" aria-hidden="true" tabindex="-1"></a>  <span class="fu">scale_fill_viridis_c</span>(<span class="at">option =</span> <span class="st">"plasma"</span>, <span class="at">name =</span> <span class="st">"Mean Weight (lbs)"</span>) <span class="sc">+</span>  <span class="co"># Gradient for weight</span></span>
<span id="cb27-35"><a href="#cb27-35" aria-hidden="true" tabindex="-1"></a>  <span class="fu">scale_y_continuous</span>(<span class="at">breaks =</span> <span class="sc">-</span><span class="fu">max</span>(quilt_summary<span class="sc">$</span>rank)<span class="sc">:</span> <span class="sc">-</span><span class="dv">1</span>, <span class="at">labels =</span> <span class="fu">max</span>(quilt_summary<span class="sc">$</span>rank)<span class="sc">:</span><span class="dv">1</span>) <span class="sc">+</span>  <span class="co"># Reverse y for top=best</span></span>
<span id="cb27-36"><a href="#cb27-36" aria-hidden="true" tabindex="-1"></a>  <span class="fu">labs</span>(</span>
<span id="cb27-37"><a href="#cb27-37" aria-hidden="true" tabindex="-1"></a>    <span class="at">title =</span> <span class="st">"NBA Positions Quilt"</span>,</span>
<span id="cb27-38"><a href="#cb27-38" aria-hidden="true" tabindex="-1"></a>    <span class="at">subtitle =</span> <span class="st">"Inspired by finance performance quilts"</span>,</span>
<span id="cb27-39"><a href="#cb27-39" aria-hidden="true" tabindex="-1"></a>    <span class="at">x =</span> <span class="st">"Decade (based on year_end)"</span>,</span>
<span id="cb27-40"><a href="#cb27-40" aria-hidden="true" tabindex="-1"></a>    <span class="at">y =</span> <span class="st">"Rank (Tallest Avg Height at Top)"</span>,</span>
<span id="cb27-41"><a href="#cb27-41" aria-hidden="true" tabindex="-1"></a>    <span class="at">fill =</span> <span class="st">"Mean Weight (lbs)"</span></span>
<span id="cb27-42"><a href="#cb27-42" aria-hidden="true" tabindex="-1"></a>  ) <span class="sc">+</span></span>
<span id="cb27-43"><a href="#cb27-43" aria-hidden="true" tabindex="-1"></a>  <span class="fu">theme_minimal</span>() <span class="sc">+</span></span>
<span id="cb27-44"><a href="#cb27-44" aria-hidden="true" tabindex="-1"></a>  <span class="fu">theme</span>(</span>
<span id="cb27-45"><a href="#cb27-45" aria-hidden="true" tabindex="-1"></a>    <span class="at">panel.grid =</span> <span class="fu">element_blank</span>(),</span>
<span id="cb27-46"><a href="#cb27-46" aria-hidden="true" tabindex="-1"></a>    <span class="at">axis.text.y =</span> <span class="fu">element_text</span>(<span class="at">size =</span> <span class="dv">10</span>),</span>
<span id="cb27-47"><a href="#cb27-47" aria-hidden="true" tabindex="-1"></a>    <span class="at">axis.text.x =</span> <span class="fu">element_text</span>(<span class="at">angle =</span> <span class="dv">45</span>, <span class="at">hjust =</span> <span class="dv">1</span>, <span class="at">size =</span> <span class="dv">10</span>)  <span class="co"># Angle x labels for legibility</span></span>
<span id="cb27-48"><a href="#cb27-48" aria-hidden="true" tabindex="-1"></a>  )</span></code></pre></div><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></div>
<div class="cell-output-display">
<div>
<figure class="figure">
<p><img src="Aaron_Powell_ForLiveSession_Unit2_files/figure-html/NBA%20Quilt%20Take%202-1.png" class="img-fluid figure-img" width="672"></p>
</figure>
</div>
</div>
</div>
</section>
</section>
<section id="separate-dataset-the-educationincome.csv-dataset-has-incomes-of-randomly-selected-americans-and-their-level-of-education.-1-2-hours" class="level2">
<h2 class="anchored" data-anchor-id="separate-dataset-the-educationincome.csv-dataset-has-incomes-of-randomly-selected-americans-and-their-level-of-education.-1-2-hours">Separate dataset: The EducationIncome.csv dataset has incomes of randomly selected Americans and their level of education. (1-2 hours)</h2>
<section id="visually-test-the-claim-that-the-distribution-of-incomes-increase-mean-or-median-as-the-education-level-rises." class="level4">
<h4 class="anchored" data-anchor-id="visually-test-the-claim-that-the-distribution-of-incomes-increase-mean-or-median-as-the-education-level-rises.">Visually test the claim that the distribution of incomes increase (mean or median) as the education level rises.</h4>
<div class="cell">
<div class="code-copy-outer-scaffold"><div class="sourceCode cell-code" id="cb28"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb28-1"><a href="#cb28-1" aria-hidden="true" tabindex="-1"></a>edu_income_data <span class="ot">&lt;-</span> <span class="fu">read.csv</span>(<span class="st">"Education_Income.csv"</span>)</span>
<span id="cb28-2"><a href="#cb28-2" aria-hidden="true" tabindex="-1"></a><span class="fu">glimpse</span>(edu_income_data)</span></code></pre></div><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></div>
<div class="cell-output cell-output-stdout">
<pre><code>Rows: 2,584
Columns: 3
$ Subject    &lt;int&gt; 2, 6, 7, 8, 9, 13, 16, 17, 18, 20, 21, 22, 29, 34, 37, 38, …
$ Educ       &lt;chr&gt; "12", "16", "12", "13-15", "13-15", "16", "13-15", "13-15",…
$ Income2005 &lt;int&gt; 5500, 65000, 19000, 36000, 65000, 8000, 71000, 43000, 12000…</code></pre>
</div>
</div>
<p>Educ appears to be categorical. &lt;12 - Less than High School 12 - High School 13-15 - Some College 16 - Bachelor’s &gt;16 - Graduate Degree or higher</p>
<div class="cell">
<div class="code-copy-outer-scaffold"><div class="sourceCode cell-code" id="cb30"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb30-1"><a href="#cb30-1" aria-hidden="true" tabindex="-1"></a><span class="fu">ggplot</span>(edu_income_data, </span>
<span id="cb30-2"><a href="#cb30-2" aria-hidden="true" tabindex="-1"></a>  <span class="fu">aes</span>(</span>
<span id="cb30-3"><a href="#cb30-3" aria-hidden="true" tabindex="-1"></a>    <span class="at">x =</span> <span class="fu">factor</span>(Educ, <span class="at">levels =</span> <span class="fu">c</span>(<span class="st">"&lt;12"</span>, <span class="st">"12"</span>, <span class="st">"13-15"</span>, <span class="st">"16"</span>, <span class="st">"&gt;16"</span>)), <span class="co"># Ordering the x axis</span></span>
<span id="cb30-4"><a href="#cb30-4" aria-hidden="true" tabindex="-1"></a>    <span class="at">y =</span> Income2005</span>
<span id="cb30-5"><a href="#cb30-5" aria-hidden="true" tabindex="-1"></a>  )</span>
<span id="cb30-6"><a href="#cb30-6" aria-hidden="true" tabindex="-1"></a>)<span class="sc">+</span></span>
<span id="cb30-7"><a href="#cb30-7" aria-hidden="true" tabindex="-1"></a><span class="fu">geom_boxplot</span>(<span class="at">fill =</span> <span class="st">"lightgreen"</span>, <span class="at">outlier.shape =</span> <span class="cn">NA</span>) <span class="sc">+</span> <span class="co"># Green for money</span></span>
<span id="cb30-8"><a href="#cb30-8" aria-hidden="true" tabindex="-1"></a><span class="fu">labs</span>(<span class="at">title =</span> <span class="st">"Income by Education Level"</span>, <span class="at">x =</span> <span class="st">"Education Level"</span>, <span class="at">y =</span> <span class="st">"Income"</span>) <span class="sc">+</span></span>
<span id="cb30-9"><a href="#cb30-9" aria-hidden="true" tabindex="-1"></a><span class="fu">scale_y_continuous</span>(<span class="at">labels =</span> scales<span class="sc">::</span><span class="fu">label_number</span>()) <span class="sc">+</span> <span class="co"># smoothing outliers</span></span>
<span id="cb30-10"><a href="#cb30-10" aria-hidden="true" tabindex="-1"></a><span class="fu">coord_cartesian</span>(<span class="at">ylim =</span> <span class="fu">c</span>(<span class="dv">0</span>, <span class="dv">200000</span>)) <span class="sc">+</span> <span class="co"># Zoom in to better see distribution</span></span>
<span id="cb30-11"><a href="#cb30-11" aria-hidden="true" tabindex="-1"></a><span class="fu">theme_bw</span>()</span></code></pre></div><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></div>
<div class="cell-output-display">
<div>
<figure class="figure">
<p><img src="Aaron_Powell_ForLiveSession_Unit2_files/figure-html/income%20by%20education%20level-1.png" class="img-fluid figure-img" width="672"></p>
</figure>
</div>
</div>
</div>
<p>There is sufficient evidence to support an increase in income as education level rises.</p>
</section>
</section>

</main>
<!-- /main column -->
<script id="quarto-html-after-body" type="application/javascript">
  window.document.addEventListener("DOMContentLoaded", function (event) {
    const icon = "";
    const anchorJS = new window.AnchorJS();
    anchorJS.options = {
      placement: 'right',
      icon: icon
    };
    anchorJS.add('.anchored');
    const isCodeAnnotation = (el) => {
      for (const clz of el.classList) {
        if (clz.startsWith('code-annotation-')) {                     
          return true;
        }
      }
      return false;
    }
    const onCopySuccess = function(e) {
      // button target
      const button = e.trigger;
      // don't keep focus
      button.blur();
      // flash "checked"
      button.classList.add('code-copy-button-checked');
      var currentTitle = button.getAttribute("title");
      button.setAttribute("title", "Copied!");
      let tooltip;
      if (window.bootstrap) {
        button.setAttribute("data-bs-toggle", "tooltip");
        button.setAttribute("data-bs-placement", "left");
        button.setAttribute("data-bs-title", "Copied!");
        tooltip = new bootstrap.Tooltip(button, 
          { trigger: "manual", 
            customClass: "code-copy-button-tooltip",
            offset: [0, -8]});
        tooltip.show();    
      }
      setTimeout(function() {
        if (tooltip) {
          tooltip.hide();
          button.removeAttribute("data-bs-title");
          button.removeAttribute("data-bs-toggle");
          button.removeAttribute("data-bs-placement");
        }
        button.setAttribute("title", currentTitle);
        button.classList.remove('code-copy-button-checked');
      }, 1000);
      // clear code selection
      e.clearSelection();
    }
    const getTextToCopy = function(trigger) {
      const outerScaffold = trigger.parentElement.cloneNode(true);
      const codeEl = outerScaffold.querySelector('code');
      for (const childEl of codeEl.children) {
        if (isCodeAnnotation(childEl)) {
          childEl.remove();
        }
      }
      return codeEl.innerText;
    }
    const clipboard = new window.ClipboardJS('.code-copy-button:not([data-in-quarto-modal])', {
      text: getTextToCopy
    });
    clipboard.on('success', onCopySuccess);
    if (window.document.getElementById('quarto-embedded-source-code-modal')) {
      const clipboardModal = new window.ClipboardJS('.code-copy-button[data-in-quarto-modal]', {
        text: getTextToCopy,
        container: window.document.getElementById('quarto-embedded-source-code-modal')
      });
      clipboardModal.on('success', onCopySuccess);
    }
      var localhostRegex = new RegExp(/^(?:http|https):\/\/localhost\:?[0-9]*\//);
      var mailtoRegex = new RegExp(/^mailto:/);
        var filterRegex = new RegExp('/' + window.location.host + '/');
      var isInternal = (href) => {
          return filterRegex.test(href) || localhostRegex.test(href) || mailtoRegex.test(href);
      }
      // Inspect non-navigation links and adorn them if external
     var links = window.document.querySelectorAll('a[href]:not(.nav-link):not(.navbar-brand):not(.toc-action):not(.sidebar-link):not(.sidebar-item-toggle):not(.pagination-link):not(.no-external):not([aria-hidden]):not(.dropdown-item):not(.quarto-navigation-tool):not(.about-link)');
      for (var i=0; i<links.length; i++) {
        const link = links[i];
        if (!isInternal(link.href)) {
          // undo the damage that might have been done by quarto-nav.js in the case of
          // links that we want to consider external
          if (link.dataset.originalHref !== undefined) {
            link.href = link.dataset.originalHref;
          }
        }
      }
    function tippyHover(el, contentFn, onTriggerFn, onUntriggerFn) {
      const config = {
        allowHTML: true,
        maxWidth: 500,
        delay: 100,
        arrow: false,
        appendTo: function(el) {
            return el.parentElement;
        },
        interactive: true,
        interactiveBorder: 10,
        theme: 'quarto',
        placement: 'bottom-start',
      };
      if (contentFn) {
        config.content = contentFn;
      }
      if (onTriggerFn) {
        config.onTrigger = onTriggerFn;
      }
      if (onUntriggerFn) {
        config.onUntrigger = onUntriggerFn;
      }
      window.tippy(el, config); 
    }
    const noterefs = window.document.querySelectorAll('a[role="doc-noteref"]');
    for (var i=0; i<noterefs.length; i++) {
      const ref = noterefs[i];
      tippyHover(ref, function() {
        // use id or data attribute instead here
        let href = ref.getAttribute('data-footnote-href') || ref.getAttribute('href');
        try { href = new URL(href).hash; } catch {}
        const id = href.replace(/^#\/?/, "");
        const note = window.document.getElementById(id);
        if (note) {
          return note.innerHTML;
        } else {
          return "";
        }
      });
    }
    const xrefs = window.document.querySelectorAll('a.quarto-xref');
    const processXRef = (id, note) => {
      // Strip column container classes
      const stripColumnClz = (el) => {
        el.classList.remove("page-full", "page-columns");
        if (el.children) {
          for (const child of el.children) {
            stripColumnClz(child);
          }
        }
      }
      stripColumnClz(note)
      if (id === null || id.startsWith('sec-')) {
        // Special case sections, only their first couple elements
        const container = document.createElement("div");
        if (note.children && note.children.length > 2) {
          container.appendChild(note.children[0].cloneNode(true));
          for (let i = 1; i < note.children.length; i++) {
            const child = note.children[i];
            if (child.tagName === "P" && child.innerText === "") {
              continue;
            } else {
              container.appendChild(child.cloneNode(true));
              break;
            }
          }
          if (window.Quarto?.typesetMath) {
            window.Quarto.typesetMath(container);
          }
          return container.innerHTML
        } else {
          if (window.Quarto?.typesetMath) {
            window.Quarto.typesetMath(note);
          }
          return note.innerHTML;
        }
      } else {
        // Remove any anchor links if they are present
        const anchorLink = note.querySelector('a.anchorjs-link');
        if (anchorLink) {
          anchorLink.remove();
        }
        if (window.Quarto?.typesetMath) {
          window.Quarto.typesetMath(note);
        }
        if (note.classList.contains("callout")) {
          return note.outerHTML;
        } else {
          return note.innerHTML;
        }
      }
    }
    for (var i=0; i<xrefs.length; i++) {
      const xref = xrefs[i];
      tippyHover(xref, undefined, function(instance) {
        instance.disable();
        let url = xref.getAttribute('href');
        let hash = undefined; 
        if (url.startsWith('#')) {
          hash = url;
        } else {
          try { hash = new URL(url).hash; } catch {}
        }
        if (hash) {
          const id = hash.replace(/^#\/?/, "");
          const note = window.document.getElementById(id);
          if (note !== null) {
            try {
              const html = processXRef(id, note.cloneNode(true));
              instance.setContent(html);
            } finally {
              instance.enable();
              instance.show();
            }
          } else {
            // See if we can fetch this
            fetch(url.split('#')[0])
            .then(res => res.text())
            .then(html => {
              const parser = new DOMParser();
              const htmlDoc = parser.parseFromString(html, "text/html");
              const note = htmlDoc.getElementById(id);
              if (note !== null) {
                const html = processXRef(id, note);
                instance.setContent(html);
              } 
            }).finally(() => {
              instance.enable();
              instance.show();
            });
          }
        } else {
          // See if we can fetch a full url (with no hash to target)
          // This is a special case and we should probably do some content thinning / targeting
          fetch(url)
          .then(res => res.text())
          .then(html => {
            const parser = new DOMParser();
            const htmlDoc = parser.parseFromString(html, "text/html");
            const note = htmlDoc.querySelector('main.content');
            if (note !== null) {
              // This should only happen for chapter cross references
              // (since there is no id in the URL)
              // remove the first header
              if (note.children.length > 0 && note.children[0].tagName === "HEADER") {
                note.children[0].remove();
              }
              const html = processXRef(null, note);
              instance.setContent(html);
            } 
          }).finally(() => {
            instance.enable();
            instance.show();
          });
        }
      }, function(instance) {
      });
    }
        let selectedAnnoteEl;
        const selectorForAnnotation = ( cell, annotation) => {
          let cellAttr = 'data-code-cell="' + cell + '"';
          let lineAttr = 'data-code-annotation="' +  annotation + '"';
          const selector = 'span[' + cellAttr + '][' + lineAttr + ']';
          return selector;
        }
        const selectCodeLines = (annoteEl) => {
          const doc = window.document;
          const targetCell = annoteEl.getAttribute("data-target-cell");
          const targetAnnotation = annoteEl.getAttribute("data-target-annotation");
          const annoteSpan = window.document.querySelector(selectorForAnnotation(targetCell, targetAnnotation));
          const lines = annoteSpan.getAttribute("data-code-lines").split(",");
          const lineIds = lines.map((line) => {
            return targetCell + "-" + line;
          })
          let top = null;
          let height = null;
          let parent = null;
          if (lineIds.length > 0) {
              //compute the position of the single el (top and bottom and make a div)
              const el = window.document.getElementById(lineIds[0]);
              top = el.offsetTop;
              height = el.offsetHeight;
              parent = el.parentElement.parentElement;
            if (lineIds.length > 1) {
              const lastEl = window.document.getElementById(lineIds[lineIds.length - 1]);
              const bottom = lastEl.offsetTop + lastEl.offsetHeight;
              height = bottom - top;
            }
            if (top !== null && height !== null && parent !== null) {
              // cook up a div (if necessary) and position it 
              let div = window.document.getElementById("code-annotation-line-highlight");
              if (div === null) {
                div = window.document.createElement("div");
                div.setAttribute("id", "code-annotation-line-highlight");
                div.style.position = 'absolute';
                parent.appendChild(div);
              }
              div.style.top = top - 2 + "px";
              div.style.height = height + 4 + "px";
              div.style.left = 0;
              let gutterDiv = window.document.getElementById("code-annotation-line-highlight-gutter");
              if (gutterDiv === null) {
                gutterDiv = window.document.createElement("div");
                gutterDiv.setAttribute("id", "code-annotation-line-highlight-gutter");
                gutterDiv.style.position = 'absolute';
                const codeCell = window.document.getElementById(targetCell);
                const gutter = codeCell.querySelector('.code-annotation-gutter');
                gutter.appendChild(gutterDiv);
              }
              gutterDiv.style.top = top - 2 + "px";
              gutterDiv.style.height = height + 4 + "px";
            }
            selectedAnnoteEl = annoteEl;
          }
        };
        const unselectCodeLines = () => {
          const elementsIds = ["code-annotation-line-highlight", "code-annotation-line-highlight-gutter"];
          elementsIds.forEach((elId) => {
            const div = window.document.getElementById(elId);
            if (div) {
              div.remove();
            }
          });
          selectedAnnoteEl = undefined;
        };
          // Handle positioning of the toggle
      window.addEventListener(
        "resize",
        throttle(() => {
          elRect = undefined;
          if (selectedAnnoteEl) {
            selectCodeLines(selectedAnnoteEl);
          }
        }, 10)
      );
      function throttle(fn, ms) {
      let throttle = false;
      let timer;
        return (...args) => {
          if(!throttle) { // first call gets through
              fn.apply(this, args);
              throttle = true;
          } else { // all the others get throttled
              if(timer) clearTimeout(timer); // cancel #2
              timer = setTimeout(() => {
                fn.apply(this, args);
                timer = throttle = false;
              }, ms);
          }
        };
      }
        // Attach click handler to the DT
        const annoteDls = window.document.querySelectorAll('dt[data-target-cell]');
        for (const annoteDlNode of annoteDls) {
          annoteDlNode.addEventListener('click', (event) => {
            const clickedEl = event.target;
            if (clickedEl !== selectedAnnoteEl) {
              unselectCodeLines();
              const activeEl = window.document.querySelector('dt[data-target-cell].code-annotation-active');
              if (activeEl) {
                activeEl.classList.remove('code-annotation-active');
              }
              selectCodeLines(clickedEl);
              clickedEl.classList.add('code-annotation-active');
            } else {
              // Unselect the line
              unselectCodeLines();
              clickedEl.classList.remove('code-annotation-active');
            }
          });
        }
    const findCites = (el) => {
      const parentEl = el.parentElement;
      if (parentEl) {
        const cites = parentEl.dataset.cites;
        if (cites) {
          return {
            el,
            cites: cites.split(' ')
          };
        } else {
          return findCites(el.parentElement)
        }
      } else {
        return undefined;
      }
    };
    var bibliorefs = window.document.querySelectorAll('a[role="doc-biblioref"]');
    for (var i=0; i<bibliorefs.length; i++) {
      const ref = bibliorefs[i];
      const citeInfo = findCites(ref);
      if (citeInfo) {
        tippyHover(citeInfo.el, function() {
          var popup = window.document.createElement('div');
          citeInfo.cites.forEach(function(cite) {
            var citeDiv = window.document.createElement('div');
            citeDiv.classList.add('hanging-indent');
            citeDiv.classList.add('csl-entry');
            var biblioDiv = window.document.getElementById('ref-' + cite);
            if (biblioDiv) {
              citeDiv.innerHTML = biblioDiv.innerHTML;
            }
            popup.appendChild(citeDiv);
          });
          return popup.innerHTML;
        });
      }
    }
  });
  </script>
</div> <!-- /content -->




</body></html>