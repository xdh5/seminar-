---
# try also 'default' to start simple
# theme: seriph
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
# background: https://cover.sli.dev
# some information about your slides (markdown enabled)
title: Seminar
info: |
  Seminar
# apply UnoCSS classes to the current slide
class: text-center
# https://sli.dev/features/drawing
drawings:
  persist: false
# slide transition: https://sli.dev/guide/animations.html#slide-transitions
# transition: slide-left
# enable MDC Syntax: https://sli.dev/features/mdc
mdc: true
---

## A genetic algorithm for minimizing energy consumption in warehouses

<div class="mt-12 py-1" hover:bg="white op-10">
  Zhao Zhiyu
</div>

<!--
Hello everyone. My name is Zhao Zhiyu.
My research is about helping robots find the best path in a busy warehouse.
-->

---
theme: seriph
layout: default
---


## Paper Reading Plan

<br/>

### Last Week

* **Paper:** *A genetic algorithm for minimizing energy consumption in warehouses*
* **Focus:** Understanding the basic concepts, core types, and main algorithms of path planning.

<br/>

### This Week

* **Paper:** *A genetic algorithm for minimizing energy consumption in warehouses*
* **Focus:** Understanding Solution methodology and Numerical experiments.

<br/>

### Next Week

* **Paper:** *A mixing algorithm of ACO and ABC for solving path planning of mobile robot*
* **Focus:** Understanding the Grid environment model and Improved ACO-ABC algorithm.

---
# 这是一个注释：使用 'layout: default' 布局
layout: default
---

# Table of Contents

<div class="grid grid-cols-2 gap-10">

<div>

* <strong class="text-xl">1. Introduction</strong>
    <br><span class="opacity-75">Why we study this problem (the "green" goal).</span>

* <strong class="text-xl">2. Literature review</strong>
    <br><span class="opacity-75">What old studies did vs. our new idea.</span>

* <strong class="text-xl">3. Problem description</strong>
    <br><span class="opacity-75">The warehouse layout and forklift speeds.</span>

* <strong class="text-xl">4. Solution methodology</strong>
    <br><span class="opacity-75">How our Genetic Algorithm (GA) works.</span>

</div>

<div>

* <strong class="text-xl">5. Numerical experiments</strong>
    <br><span class="opacity-75">Testing the GA and showing the results.</span>

* <strong class="text-xl">6. Conclusions</strong>
    <br><span class="opacity-75">What we learned and what to do next.</span>

</div>

</div>

---
layout: default
---

# Solution Methodology

<div class="grid grid-cols-1 gap-4 mt-8 text-sm">

<div class="p-4 bg-blue-50 border-l-4 border-blue-600 rounded">
  <h3 class="text-base font-bold text-blue-800 mb-2">Basics of Genetic Algorithms</h3>
  <ul class="list-disc pl-4 space-y-1 leading-snug text-gray-700">
    <li>"Search algorithms based on <strong>natural selection and genetics</strong>".</li>
    <li>"Founds on a <strong>population of candidate solutions</strong> differently from traditional search methods".</li>
    <li>Key Requirements: "<strong>Encoding</strong> the potential solutions and defining the <strong>fitness function</strong>".</li>
  </ul>
</div>

<div class="p-4 bg-green-50 border-l-4 border-green-600 rounded">
  <h3 class="text-base font-bold text-green-800 mb-2">Chromosome Encoding</h3>
  <p class="mb-3 text-gray-700">
    "Encoded through a string composed of orders locations".
  </p>
  
  <div class="grid grid-cols-[80px_1fr] gap-2 text-gray-800">
    <span class="font-bold text-right mr-2">Gene:</span>
    <span>"Represents <strong>location numbers</strong> of the orders".</span>
    <span class="font-bold text-right mr-2">Position:</span>
    <span>"Represents <strong>batch number</strong> that the order belongs".</span>
  </div>
</div>

</div>

---
layout: default
---

# Fitness Function & Energy Calculation

<div class="flex flex-col gap-4 mt-6 text-sm">

<!-- Objective Function Section -->
<div class="p-4 bg-blue-50 border-l-4 border-blue-600 rounded shadow-sm">
<h3 class="text-base font-bold text-blue-800 mb-1">Objective Function</h3>
<p class="text-gray-700">
The fitness function evaluates solution quality. The objective is <strong>minimizing total energy consumption</strong> for order picking.
</p>
</div>

<!-- Energy Estimation Model Section -->
<div class="p-4 bg-green-50 border-l-4 border-green-600 rounded shadow-sm">
<h3 class="text-base font-bold text-green-800 mb-3">Energy Estimation Model</h3>
  
<div class="grid grid-cols-[1.5fr_1fr] gap-4">

<!-- Variables Column -->
<div>
<p class="text-gray-700 mb-2">Calculated based on electric forklift data, considering:</p>

<!-- 这里改用了 Markdown 列表，并用 div 包裹以应用样式 -->
<div class="text-gray-800 leading-tight pl-4">

- $Dis_h$ / $Dis_v$: Horizontal / Vertical travel distance
- $v_h$ / $v_v$: Horizontal / Vertical speed of forklift
- $uc_e$: Unit energy consumption ($uc_e$)

</div>
</div>

<!-- Formula Column -->
<div class="flex flex-col justify-center items-center bg-white rounded border border-green-200 p-3 shadow-inner">
<div class="text-[10px] text-gray-500 font-mono mb-1 uppercase tracking-wider">Calculation Formula</div>
<div class="text-base text-gray-900 py-2">

$$
E = \left[ \frac{Dis_h}{v_h} + \frac{Dis_v}{v_v} \right] \times uc_e
$$

</div>
</div>
    
</div>
</div>

</div>

---
layout: default
---

# Genetic Operators

<div class="grid grid-cols-3 gap-6 mt-10 text-sm">

<!-- Selection Operator -->
<div class="bg-red-50 p-5 rounded border-t-4 border-red-500 shadow-sm">
<h3 class="text-lg font-bold text-red-800 mb-3">1. Selection</h3>
<p class="font-bold text-gray-700 mb-2">Roulette Wheel Selection</p>
<p class="text-gray-600 leading-relaxed">
Chromosomes with higher fitness have a greater chance of being selected for the next generation.
</p>
</div>

<!-- Crossover Operator -->
<div class="bg-blue-50 p-5 rounded border-t-4 border-blue-500 shadow-sm">
<h3 class="text-lg font-bold text-blue-800 mb-3">2. Crossover</h3>
<p class="font-bold text-gray-700 mb-2">Reverse Action Crossover</p>
<p class="text-gray-600 leading-relaxed mb-3">
Randomly select two cut-points and reverse the gene sequence between them to generate a new chromosome.
</p>
<div class="text-xs text-blue-700 font-mono bg-blue-100 inline-block px-2 py-1 rounded border border-blue-200">
Goal: Exploit search space
</div>
</div>

<!-- Mutation Operator -->
<div class="bg-green-50 p-5 rounded border-t-4 border-green-500 shadow-sm">
<h3 class="text-lg font-bold text-green-800 mb-3">3. Mutation</h3>
<p class="font-bold text-gray-700 mb-2">Swap Mutation</p>
<p class="text-gray-600 leading-relaxed mb-3">
Randomly select two genes and swap their positions.
</p>
<div class="text-xs text-green-700 font-mono bg-green-100 inline-block px-2 py-1 rounded border border-green-200">
Goal: Explore search space
</div>
</div>

</div>

---
layout: default
---

# Experimental Setup & Performance

<!-- 这里的 h-[400px] 限制了内容区域高度，防止撑满全屏 -->
<div class="grid grid-cols-2 gap-5 mt-4 text-sm">

<!-- Left Column -->
<div class="flex flex-col gap-4">

<!-- Box 1: Environment -->
<div class="p-3 bg-blue-50 border-l-4 border-blue-600 rounded shadow-sm">
<h3 class="font-bold text-blue-800 mb-1 text-base">Experimental Environment</h3>
<ul class="list-disc pl-4 space-y-1 text-gray-700 leading-snug">
<li><strong>Storage Policy:</strong> Adopts Class-based storage policy (reduces travel distance).</li>
<li><strong>Implementation:</strong> C# programming language in Microsoft Visual Studio.</li>
</ul>
</div>

<!-- Box 2: Parameters (表格更紧凑) -->
<div class="p-3 bg-white border border-gray-200 rounded shadow-sm flex-grow">
<h3 class="font-bold text-gray-800 mb-2 border-b pb-1 text-base">Parameter Settings</h3>
<table class="w-full text-left border-collapse text-xs">
<tr class="border-b border-gray-100"><td class="py-1 text-gray-600">Population Size</td><td class="font-mono text-blue-700 text-right">125</td></tr>
<tr class="border-b border-gray-100"><td class="py-1 text-gray-600">Crossover Rate</td><td class="font-mono text-blue-700 text-right">0.7</td></tr>
<tr class="border-b border-gray-100"><td class="py-1 text-gray-600">Mutation Rate</td><td class="font-mono text-blue-700 text-right">0.008</td></tr>
<tr><td class="py-1 text-gray-600">Elitism Rate</td><td class="font-mono text-blue-700 text-right">0.04</td></tr>
</table>
</div>

</div>

<!-- Right Column: Results (间距缩小) -->
<div class="p-4 bg-green-50 border-l-4 border-green-600 rounded shadow-sm">
<h3 class="font-bold text-green-800 mb-3 text-base">Convergence & Termination</h3>

<div class="space-y-3">
  <div>
    <p class="font-bold text-gray-800 text-xs uppercase tracking-wider mb-0.5">Convergence Behavior</p>
    <p class="text-gray-700 leading-snug">
      The algorithm shows <strong>rapid fitness improvement</strong> in early iterations before stabilizing.
    </p>
  </div>

  <div>
    <p class="font-bold text-gray-800 text-xs uppercase tracking-wider mb-0.5">Termination Condition</p>
    <p class="text-gray-700 leading-snug">
      Stops if fitness improvement is <strong>< 0.001</strong> over <strong>200 iterations</strong>.
    </p>
  </div>

  <div>
    <p class="font-bold text-gray-800 text-xs uppercase tracking-wider mb-0.5">Performance Result</p>
    <p class="text-gray-700 leading-snug">
      Provides effective solutions in <strong>short CPU times</strong> even for large-scale datasets.
    </p>
  </div>
</div>

</div>

</div>

---
layout: default
---

# Comparative Results: GA vs. FCFS

<div class="grid grid-cols-2 gap-6 mt-6 text-sm">

<!-- Left Column: Comparison & Trends -->
<div class="flex flex-col gap-5">

<!-- Benchmark Section -->
<div class="p-4 bg-blue-50 border-l-4 border-blue-600 rounded shadow-sm">
<h3 class="font-bold text-blue-800 mb-2">Benchmark Strategy</h3>
<p class="text-gray-700 leading-snug">
Comparison between the proposed <strong>Genetic Algorithm (GA)</strong> and the traditional <strong>First-Come-First-Served (FCFS)</strong> strategy.
</p>
</div>

<!-- Findings Section -->
<div class="p-4 bg-white border border-gray-200 rounded shadow-sm flex-grow">
<h3 class="font-bold text-gray-800 mb-3 border-b pb-2">Experimental Findings</h3>
<ul class="list-disc pl-4 space-y-3 text-gray-700 leading-snug">
<li>
<strong>Consistent Reduction:</strong><br>
GA energy consumption is significantly lower than FCFS across all datasets (DS1 - DS10).
</li>
<li>
<strong>Scaling Efficiency:</strong><br>
Energy savings become more pronounced as the <strong>number of orders increases</strong>.
</li>
</ul>
</div>

</div>

<!-- Right Column: Quantified Benefits -->
<div class="flex flex-col gap-5">

<div class="p-5 bg-green-50 border-l-4 border-green-600 rounded shadow-sm h-full flex flex-col justify-center">
<h3 class="font-bold text-green-800 mb-6">Quantified Benefits</h3>

<!-- Stat Highlight -->
<div class="bg-white p-6 rounded-lg border border-green-100 shadow-inner text-center mb-6">
<p class="text-xs text-gray-500 uppercase tracking-widest mb-2">Annual Energy Saving Rate</p>
<p class="text-5xl font-bold text-green-600 mb-2">~23.5%</p>
<p class="text-xs text-gray-400">*Based on Low Order Rate (40 orders/h)</p>
</div>

<!-- Impact Statement -->
<div>
<p class="font-bold text-gray-700 mb-1">Global Potential</p>
<p class="text-gray-600 leading-snug">
Demonstrates significant potential for large-scale energy conservation in warehouse operations globally.
</p>
</div>

</div>

</div>

</div>

---
layout: default
---

# Batch Size & Sensitivity Analysis

<div class="grid grid-cols-2 gap-4 mt-2 text-sm">

<div class="flex flex-col gap-2">

<div class="p-3 bg-blue-50 border-l-4 border-blue-600 rounded shadow-sm">
<h4 class="font-bold text-blue-800 mb-1 text-base">Experiment Setup</h4>
<p class="text-gray-700 leading-snug text-xs">
Tested the effect of different <strong>batch sizes (1 to 6)</strong> on total energy consumption using dataset DS3.
</p>
</div>

<div class="p-3 bg-white border border-gray-200 rounded shadow-sm flex-grow">
<h4 class="font-bold text-gray-800 mb-2 border-b pb-1 text-base">Key Findings</h4>
<ul class="list-disc pl-4 space-y-2 text-gray-700 leading-snug text-xs">
<li>
<strong>Significant Impact:</strong><br>
Batch size has a reasonable and significant effect on total energy consumption.
</li>
<li>
<strong>Optimal Size:</strong><br>
Minimum energy consumption is achieved at <strong>Batch Size = 2</strong> in this warehouse setting.
</li>
<li>
<strong>Trend:</strong><br>
Energy consumption <strong>increases</strong> as batch size grows beyond 2.
</li>
</ul>
</div>

</div>

<div class="p-4 bg-green-50 border-l-4 border-green-600 rounded shadow-sm h-full">
<h3 class="font-bold text-green-800 mb-4 text-base">Warehouse Scalability</h3>

<div class="space-y-5">
<div>
<p class="font-bold text-gray-800 text-xs uppercase tracking-wider mb-1">Test Scenarios</p>
<p class="text-gray-700 leading-snug text-xs">
Algorithm was tested on warehouses with varying characteristics, ranging from <strong>1200 to 2800 storage locations</strong>.
</p>
</div>

<div>
<p class="font-bold text-gray-800 text-xs uppercase tracking-wider mb-1">Adaptability Result</p>
<p class="text-gray-700 leading-snug text-xs">
While energy consumption increases slightly with warehouse size, the algorithm <strong>remains effective</strong> across all configurations.
</p>
</div>
</div>

</div>

</div>

---
layout: default
---

# Conclusions

<div class="grid grid-cols-3 gap-5 mt-8 text-sm">

<div class="p-4 bg-blue-50 border-l-4 border-blue-600 rounded shadow-sm">
<h3 class="font-bold text-blue-800 mb-3 text-base">Research Summary</h3>
<ul class="list-disc pl-4 space-y-3 text-gray-700 leading-snug">
<li>
<strong>Energy Focus:</strong><br>
Unlike previous studies on time or distance, this study focuses on <strong>minimizing energy consumption</strong> in manual warehouses.
</li>
<li>
<strong>Green Integration:</strong><br>
Integrates environmental thinking into warehouse operations management.
</li>
</ul>
</div>

<div class="p-4 bg-green-50 border-l-4 border-green-600 rounded shadow-sm">
<h3 class="font-bold text-green-800 mb-3 text-base">Main Contributions</h3>
<ul class="list-disc pl-4 space-y-3 text-gray-700 leading-snug">
<li>
<strong>Algorithm Development:</strong><br>
Developed a Genetic Algorithm that combines <strong>order batching</strong> and <strong>routing optimization</strong>.
</li>
<li>
<strong>Performance:</strong><br>
Proven to have <strong>high computational efficiency</strong> and is adaptable to different types of warehouses.
</li>
</ul>
</div>

<div class="p-4 bg-purple-50 border-l-4 border-purple-600 rounded shadow-sm">
<h3 class="font-bold text-purple-800 mb-3 text-base">Future Directions</h3>
<p class="text-gray-700 leading-snug mb-2">
Design a comprehensive <strong>Decision Support System</strong> integrating:
</p>
<ul class="list-disc pl-4 space-y-1 text-gray-700 text-xs mb-3">
<li>Storage Assignment</li>
<li>Order Batching</li>
<li>Routing Optimization</li>
</ul>
<p class="text-gray-700 leading-snug">
<strong>Goal:</strong> Achieve environmentally sustainable warehouse operations.
</p>
</div>

</div>