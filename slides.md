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

## Path planning techniques for mobile robots: Review and prospect

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

* **Paper:** *Path planning techniques for mobile robots: Review and prospect*
* **Focus:** Understanding the core concepts of global vs. local planning (Chapter 2).

<br/>

### This Week

* **Paper:** *Path planning techniques for mobile robots: Review and prospect*
* **Focus:** Moving on to the "Algorithms" section (Chapter 3) of the paper.

<br/>

### Next Week

* **Paper:** *A genetic algorithm for minimizing energy consumption in warehouses*
* **Focus:** Understanding the basic concepts, core types, and main algorithms of path planning.

---
layout: center
---

# How Robots Find Their Way! 

<div class="grid grid-cols-3 gap-8 text-center mt-8">

<div>
  <h2 class="text-3xl">1. Classical Algorithms </h2>
  <p class="mt-4">
    These are the first and oldest ways to help a robot. They follow simple rules to find the best path.
  </p>
  <ul class="list-none mt-4">
    <li>Dijkstra</li>
    <li>A*</li>
    <li>RRT</li>
    <li>APF</li>
  </ul>
</div>

<div>
  <h2 class="text-3xl">2. Bionic Algorithms </h2>
  <p class="mt-4">
    We learn from animals! These methods copy how ants find food or how birds fly together.
  </p>
  <ul class="list-none mt-4">
    <li>Ants Teamwork</li>
    <li>Bird Flocks</li>
  </ul>
</div>

<div>
  <h2 class="text-3xl">3. AI Algorithms </h2>
  <p class="mt-4">
    We give the robot a brain to think and learn. It can make its own smart choices!
  </p>
  <ul class="list-none mt-4">
    <li>"Maybe" Logic (Fuzzy Logic)</li>
    <li>Robot Brain (Neural Network)</li>
  </ul>
</div>

</div>

---
---

# 1. Classic Algorithms

<div class="grid grid-cols-3 gap-8 mt-8">

<div>
  <h2 class="text-2xl font-bold">Cell Decomposition</h2>
  <ul class="mt-4 space-y-2">
    <li><b>How it works:</b> Breaks the world into small, simple squares. The robot finds a path using these squares.</li>
    <li class="mt-2"><b>Why it's good:</b> It is simple and easy to use. It is the most popular way to make a map.</li>
  </ul>
</div>

<div>
  <h2 class="text-2xl font-bold">Graph Search Algorithm (GSA)</h2>
  <ul class="mt-4 space-y-2">
    <li><b>Dijkstra:</b> Checks all the nodes. It always finds the best path, but it is very slow.</li>
    <li class="mt-2"><b>A* (A-star):</b> A smarter way. It "guesses" how far the end is. This makes it much faster. It is a key tool for path planning.</li>
  </ul>
</div>

<div>
  <h2 class="text-2xl font-bold">Sampling Based Method (SBM)</h2>
  <ul class="mt-4 space-y-2">
    <li><b>RRT (Rapidly-exploring Random Tree):</b> "Grows" a random tree to explore the map. It is good at finding a path in big, complex spaces.</li>
    <li class="mt-2"><b>PRM (Probabilistic Roadmap):</b> Puts many random dots on the map. It then tries to connect the dots to make a road map.</li>
  </ul>
</div>

</div>

---
---

# 1. Classic Algorithms

<div class="grid grid-cols-2 gap-8 mt-10">

<div>
  <h2 class="text-2xl font-bold">Artificial Potential Field (APF)</h2>
  <ul class="mt-4 space-y-2">
    <li><b>How it works:</b> The robot is in a "force field".
      <ul class="list-disc pl-6 mt-2">
        <li>The <b>Goal</b> pulls the robot.</li>
        <li><b>Obstacles</b> push the robot.</li>
      </ul>
    </li>
    <li class="mt-4"><b>Good parts:</b> The path is smooth. It thinks fast. It is very good for avoid new things.</li>
    <li class="mt-4"><b>Bad parts:</b> The robot can get "stuck" in a trap or "cannot reach the goal".</li>
  </ul>
</div>

<div>
  <h2 class="text-2xl font-bold">Dynamic Window Approach (DWA)</h2>
  <ul class="mt-4 space-y-2">
    <li><b>How it works:</b> A popular way to plan local paths.</li>
    <li class="mt-4"><b>What it does:</b> It thinks hard about the robot's <b>body rules</b> . It "imagines" many local paths it can take. Then, it picks the best one.</li>
  </ul>
</div>

</div>

---
---

# 2. Bionic Algorithms

<p class="mt-4">
  <b>Main Idea:</b> We copy smart group behaviors from nature to solve hard problems.
</p>

<div class="grid grid-cols-3 gap-6 mt-8 text-center">

<div>
  <h2 class="font-bold">ACO</h2>
  <p class="mt-2">
    Copies how <b>ants</b> use trails to find the shortest path.
  </p>
</div>

<div>
  <h2 class="font-bold">GA</h2>
  <p class="mt-2">
    Copies <b>"survival of the fittest"</b> (selection, crossover, mutation) to find better paths.
  </p>
</div>

<div>
  <h2 class="font-bold">PSO</h2>
  <p class="mt-2">
    Copies how <b>birds</b> search for food. They share the "best spot" with the group.
  </p>
</div>

</div>

<div classs="mt-10">
  <h2 class="text-xl font-bold text-center mt-10">Other Algorithms</h2>
  <p class="text-center mt-2">
    Like Bacterial Foraging (BFO), Sparrow Search (SSA), Grey Wolf Optimizer (GWO), etc.
  </p>
</div>

---
---
# 3. AI Algorithms

<p class="mt-4 text-xl">
<b>Main Idea:</b> We give the robot a "brain" to learn, think, and make smart decisions.
</p>

<div class="grid grid-cols-2 gap-8 mt-10">

<div>
<h2 class="text-2xl font-bold">Fuzzy Logic (FL)</h2>
<ul class="mt-4 space-y-2">
<li><b>How it works:</b> Copies how people think and drive using "fuzzy" ideas.</li>
<li><b>Example:</b> It changes "Distance is 2.5 meters" into "Very Close". Then it uses a rule like "If 'Very Close', then true.</li>
<li><b>Good for:</b> Handling sensor noise and unknown areas.</li>
</ul>
</div>

<div>
<h2 class="text-2xl font-bold">Bioinspired Neural Network (BNN)</h2>
<ul class="mt-4 space-y-2">
<li><b>How it works:</b> Uses a neural network's dynamic power to plan a path.</li>
<li><b>Special thing:</b> The BNN in the paper <b>does not need to learn first</b>. It finds a path very fast by passing messages.</li>
</ul>
</div>

</div>

---
---
<p class="mt-4 text-lg">
Based on 105 papers, here is what we found:
</p>

<div class="mt-8 space-y-6">

<div>
<h2 class="text-xl font-bold">How to Make Maps:</h2>
<ul class="list-disc pl-6 mt-2">
<li><b>Grid Method</b> is the clear winner (85.7%). It is simple and easy to make bigger.</li>
</ul>
</div>

<div>
<h2 class="text-xl font-bold">How to Use Algorithms:</h2>
<ul class="list-disc pl-6 mt-2">
<li>For <b>Global Planning</b>, people like <b>Classic Algorithms</b> (like A*, RRT).</li>
<li>For <b>Local Planning</b>, people use <b>AI</b> and <b>Bionic Algorithms</b>.</li>
</ul>
</div>

<div>
<h2 class="text-xl font-bold">What is Missing:</h2>
<ul class="list-disc pl-6 mt-2">
<li><b>Dimension:</b> Most research is for <b>2D</b>. Not much work is done for <b>3D</b>.</li>
<li><b>Testing:</b> Most tests are on a <b>computer simulation</b>. Not many tests are on a <b>real robot</b>.</li>
<li><b>New Ideas:</b> Most work makes one algorithm better. Not much work mixes algorithms.</li>
</ul>
</div>

</div>

---
---
# What's Next?
<ul class="mt-8 space-y-4 text-xl">

<li>
<b>1. Algorithm Fusion</b>
<p class="text-lg ml-6">
Mix algorithms to get the best parts of each.





(Example: Use <b>A*</b> for the big plan, and <b>DWA</b> or <b>APF</b> for local avoid.)
</p>
</li>

<li>
<b>2. Global + Local</b>
<p class="text-lg ml-6">
Connect the big plan (Global) with what the robot sees right now (Local feedback).
</p>
</li>

<li>
<b>3. Adding Learning</b>
<p class="text-lg ml-6">
Add learning (like <b>Reinforcement Learning</b>). This helps robots adapt to new, busy places, like a mall.
</p>
</li>

<li>
<b>4. Multi-Robot Collaboration</b>
<p class="text-lg ml-6">
Plan paths for <i>many</i> robots so they don't crash. This is a big challenge for warehouses and delivery.
</p>
</li>

</ul>