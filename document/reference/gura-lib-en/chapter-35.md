---
layout: doc-widenavi
lang: en
title: Gura Library Reference
prevpage: chapter-34.html#naviitem-selected
nextpage: chapter-36.html#naviitem-selected
---
{% raw %}
<h1><span class="caption-index-1">35</span>ml.linear Module</h1>
<h2><span class="caption-index-2">35.1</span><a name="anchor-35-1"></a>Overview</h2>
<h2><span class="caption-index-2">35.2</span><a name="anchor-35-2"></a>ml.linear.feature Class</h2>
<h3><span class="caption-index-3">35.2.1</span><a name="anchor-35-2-1"></a>Property</h3>
<p>
A <code class="highlighter-rouge">ml.linear.feature</code> instance has the following properties:
</p>
<h3><span class="caption-index-3">35.2.2</span><a name="anchor-35-2-2"></a>Constructor</h3>
<p>
<div class="h5">linear.feature</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>linear.feature(x[]:list) {block?}</code></div>
Creates an instance of ml.linear.feature.
</p>
<h3><span class="caption-index-3">35.2.3</span><a name="anchor-35-2-3"></a>Method</h3>
<h2><span class="caption-index-2">35.3</span><a name="anchor-35-3"></a>ml.linear.model Class</h2>
<h3><span class="caption-index-3">35.3.1</span><a name="anchor-35-3-1"></a>Property</h3>
<p>
A <code class="highlighter-rouge">ml.linear.model</code> instance has the following properties:
</p>
<h3><span class="caption-index-3">35.3.2</span><a name="anchor-35-3-2"></a>Method</h3>
<p>
<div class="h5">linear.model#predict</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>linear.model#predict(feature:linear.feature):map</code></div>

</p>
<p>
<div class="h5">linear.model#predict_probability</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>linear.model#predict_probability(feature:linear.feature):map</code></div>

</p>
<p>
<div class="h5">linear.model#get_nr_feature</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>linear.model#get_nr_feature()</code></div>

</p>
<p>
<div class="h5">linear.model#get_nr_class</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>linear.model#get_nr_class()</code></div>

</p>
<p>
<div class="h5">linear.model#get_labels</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>linear.model#get_labels()</code></div>

</p>
<p>
<div class="h5">linear.model#get_decfun_coef</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>linear.model#get_decfun_coef(feat_idx:number, label_idx:number)</code></div>

</p>
<p>
<div class="h5">linear.model#get_decfun_bias</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>linear.model#get_decfun_bias(label_idx:number)</code></div>

</p>
<h2><span class="caption-index-2">35.4</span><a name="anchor-35-4"></a>ml.linear.parameter Class</h2>
<h3><span class="caption-index-3">35.4.1</span><a name="anchor-35-4-1"></a>Property</h3>
<p>
A <code class="highlighter-rouge">ml.linear.parameter</code> instance has the following properties:
</p>
<h3><span class="caption-index-3">35.4.2</span><a name="anchor-35-4-2"></a>Constructor</h3>
<p>
<div class="h5">linear.parameter</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>linear.parameter() {block?}</code></div>
Creates an instance of ml.linear.parameter.
</p>
<h3><span class="caption-index-3">35.4.3</span><a name="anchor-35-4-3"></a>Method</h3>
<p>
<div class="h5">linear.parameter#add_weight</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>linear.parameter#add_weight(label:number, weight:number):reduce</code></div>

</p>
<h2><span class="caption-index-2">35.5</span><a name="anchor-35-5"></a>ml.linear.problem Class</h2>
<h3><span class="caption-index-3">35.5.1</span><a name="anchor-35-5-1"></a>Property</h3>
<p>
A <code class="highlighter-rouge">ml.linear.problem</code> instance has the following properties:
</p>
<h3><span class="caption-index-3">35.5.2</span><a name="anchor-35-5-2"></a>Constructor</h3>
<p>
<div class="h5">linear.problem</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>linear.problem() {block?}</code></div>
Creates an instance of ml.linear.problem.
</p>
<h3><span class="caption-index-3">35.5.3</span><a name="anchor-35-5-3"></a>Method</h3>
<p>
<div class="h5">linear.problem#add_sample</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>linear.problem#add_sample(sample:linear.sample):map:reduce</code></div>

</p>
<h2><span class="caption-index-2">35.6</span><a name="anchor-35-6"></a>ml.linear.sample Class</h2>
<h3><span class="caption-index-3">35.6.1</span><a name="anchor-35-6-1"></a>Property</h3>
<p>
A <code class="highlighter-rouge">ml.linear.sample</code> instance has the following properties:
</p>
<h3><span class="caption-index-3">35.6.2</span><a name="anchor-35-6-2"></a>Constructor</h3>
<p>
<div class="h5">linear.sample</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>linear.sample(label:number, feature:linear.feature) {block?}</code></div>
Creates an instance of ml.linear.sample.
</p>
<h2><span class="caption-index-2">35.7</span><a name="anchor-35-7"></a>Module Function</h2>
<p>
<div class="h5">linear.train</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>linear.train(prob:linear.problem, param:linear.parameter, bias?:number) {block?}</code></div>

</p>
{% endraw %}
