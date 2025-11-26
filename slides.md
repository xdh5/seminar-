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

## A mixing algorithm of ACO and ABC for solving path planning of mobile robot

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
* **Focus:** Understanding Solution methodology and Numerical experiments.

<br/>

### This Week

* **Paper:** *A mixing algorithm of ACO and ABC for solving path planning of mobile robot*
* **Focus:** Understanding the Grid environment model and Improved ACO-ABC algorithm.

<br/>

### Next Week

* **Paper:** *A mixing algorithm of ACO and ABC for solving path planning of mobile robot*
* **Focus:** Understanding the Experiments and numerical analysis.

---
# 这是一个注释：使用 'layout: default' 布局
layout: default
---

<div style="display: flex; justify-content: center">
<img style="height: 450px; width: 650px " src="./assets/e765eb7d-6fab-4cf0-8280-8c342432003a.jpg">
</div>

---
layout: center
---

<div class="w-full max-w-6xl mx-auto">

<h1 class="text-5xl font-bold mb-16 text-center text-blue-900">Table of Contents</h1>

<div class="grid grid-cols-2 gap-x-20 gap-y-12 w-full px-8">

  <div class="flex items-center border-l-4 border-gray-300 pl-4">
    <span class="text-4xl font-bold text-gray-300 mr-4">01</span>
    <span class="text-2xl font-bold text-gray-800">Introduction</span>
  </div>

  <div class="flex items-center border-l-4 border-gray-300 pl-4">
    <span class="text-4xl font-bold text-gray-300 mr-4">02</span>
    <span class="text-2xl font-bold text-gray-800">Mathematical Model of Path Planning</span>
  </div>

  <div class="flex items-center border-l-4 border-gray-300 pl-4">
    <span class="text-4xl font-bold text-gray-300 mr-4">03</span>
    <span class="text-2xl font-bold text-gray-800">Improved ACO-ABC Algorithm</span>
  </div>

  <div class="flex items-center border-l-4 border-gray-300 pl-4">
    <span class="text-4xl font-bold text-gray-300 mr-4">04</span>
    <span class="text-2xl font-bold text-gray-800">Experiments & Numerical Analysis</span>
  </div>

  <div class="flex items-center border-l-4 border-gray-300 pl-4">
    <span class="text-4xl font-bold text-gray-300 mr-4">05</span>
    <span class="text-2xl font-bold text-gray-800">Discussion</span>
  </div>

  <div class="flex items-center border-l-4 border-gray-300 pl-4">
    <span class="text-4xl font-bold text-gray-300 mr-4">06</span>
    <span class="text-2xl font-bold text-gray-800">Conclusion</span>
  </div>

</div>

</div>

---
layout: two-cols
---

# Research Objective & Modeling

### 1. Research Objective
To find an **optimal and collision-free path** for a mobile robot within the workspace.

### 2. Environment Modeling
Adopting the **Grid Method** to model the space. The environment is divided into a grid map:

* ⬛ **Black Grid**: Represents an **Obstacle**.
* ⬜ **White Grid**: Represents a **Free area**.
* 🟥 **S**: Represents the **Start point**.
* 🟦 **T**: Represents the **Target point**.

::right::

<div class="flex flex-col items-center justify-center h-full ml-4">
  <div class="border-2 border-dashed border-gray-400 rounded-lg p-6 w-full h-80 flex items-center justify-center bg-gray-50">
    <img 
      src="./assets/fig1.png" 
      class="max-h-full max-w-full object-contain" 
      alt="Fig. 1. Space environment model"
    />
  </div>
</div>

---
layout: default
---

# Research Background & Motivation

### Why combine ACO and ABC?

<div class="grid grid-cols-2 gap-16 mt-12">

<div>
  <h4 class="text-2xl text-blue-800 font-bold mb-6 border-b-2 border-blue-200 pb-2">
    Ant Colony Optimization (ACO)
  </h4>
  <div class="space-y-6 text-gray-700">
    <div>
      <span class="font-bold text-green-700 text-lg block mb-1">Pros</span>
      <span>Strong robustness.</span>
    </div>
    <div>
      <span class="font-bold text-red-700 text-lg block mb-1">Cons</span>
      <span>Slow convergence speed, blindness in the early search stage, and easy to fall into local optima.</span>
    </div>
  </div>
</div>

<div>
  <h4 class="text-2xl text-yellow-700 font-bold mb-6 border-b-2 border-yellow-200 pb-2">
    Artificial Bee Colony (ABC)
  </h4>
  <div class="space-y-6 text-gray-700">
    <div>
      <span class="font-bold text-green-700 text-lg block mb-1">Pros</span>
      <span>High search efficiency and fast convergence speed.</span>
    </div>
    <div>
      <span class="font-bold text-red-700 text-lg block mb-1">Cons</span>
      <span>Early convergence and poor initial path planning effect.</span>
    </div>
  </div>
</div>

</div>

<div class="mt-16 text-center">
  <p class="text-xl text-gray-800 bg-gray-50 py-4 rounded-lg border border-gray-200">
    <span class="font-bold text-primary">Strategy:</span> Combine the advantages of both to propose the <b>IACO-IABC algorithm</b>.
  </p>
</div>

---
layout: two-cols
---

# IACO-IABC Hybrid Strategy

<div class="mt-8 space-y-8">

<div>
  <h4 class="text-xl font-bold text-gray-800 mb-2">1. Phased Collaboration</h4>
  <ul class="list-disc list-outside ml-5 space-y-4 text-gray-700">
    <li>
      <span class="font-bold text-blue-700">Global Search (ABC):</span>
      <span>Uses improved ABC to quickly generate "Basic Nodes" of the path, determining the general direction.</span>
    </li>
    <li>
      <span class="font-bold text-blue-700">Local Connection (ACO):</span>
      <span>Uses improved ACO to find the optimal connection between these basic nodes.</span>
    </li>
  </ul>
</div>

<div>
  <h4 class="text-xl font-bold text-gray-800 mb-2">2. Advantage</h4>
  <p class="text-gray-700">
    Utilizes ABC's global search capability and ACO's path optimization capability.
  </p>
</div>

</div>

::right::

<div class="flex flex-col items-center justify-center h-full ml-6">
  <div class="border-2 border-dashed border-gray-400 rounded-lg p-4 w-full h-96 flex items-center justify-center bg-gray-50">
    <img 
      src="./assets/fig9.png" 
      class="max-h-full max-w-full object-contain" 
      alt="Fig. 9. Basic process of the IACO-IABC algorithm"
    />
  </div>
</div>

---
layout: two-cols
---

### Improvement 1: ACO Heuristic Mechanism

#### Solving the "Blind Search" Problem

<div class="mt-5 space-y-5">

<div>
  <h4 class="text-xl font-bold text-red-800 mb-3 border-l-4 border-red-600 pl-4">
    Traditional Problem
  </h4>
  <p class="text-gray-700 text-l leading-relaxed">
    Traditional heuristic functions only consider the distance between the current node and the next node. This results in <b>weak guidance</b> and leads to blind searching.
  </p>
</div>

<div>
  <h4 class="text-xl font-bold text-green-800 mb-3 border-l-4 border-green-600 pl-4">
    Improved Method
  </h4>
  <ul class="list-disc list-outside ml-6 space-y-0.1 text-gray-700 text-l leading-relaxed">
    <li>
      <span class="font-bold text-black">New Factors:</span> Incorporates <strong>Direction</strong> and <strong>Turning</strong> information into the function.
    </li>
    <li>
      <span class="font-bold text-black">Geometric Context:</span> Considers the Start, Current, and Target positions simultaneously.
    </li>
    <li>
      <span class="font-bold text-black">Goal:</span> Prioritizes nodes facing the target to reduce unnecessary turns.
    </li>
  </ul>
</div>

</div>

::right::

<div class="flex flex-col items-center justify-center h-full ml-8">
  <div class="border-2 border-dashed border-gray-400 rounded-lg p-2 w-full h-80 flex items-center justify-center bg-gray-50">
    <img 
      src="./assets/fig3.png" 
      class="max-h-full max-w-full object-contain" 
      alt="Fig. 3. Comparison of heuristic information"
    />
  </div>
</div>

---
layout: two-cols
---

### Improvement 2: ABC Search Mechanism

#### Enhancing Search Efficiency

<div class="mt-5 space-y-5">

<div>
  <h4 class="text-x font-bold text-blue-800 mb-3 border-l-4 border-blue-600 pl-4">
    Employed Bees
  </h4>
  <ul class="list-disc list-outside ml-6 space-y-0 text-gray-700 text-m leading-relaxed">
    <li>
      <span class="font-bold text-black">Mechanism:</span> 
      <strong>Shrinking Encircling</strong>.
    </li>
    <li>
      <span class="font-bold text-black">Effect:</span> 
      As iterations increase, the search range gradually shrinks towards the global optimal solution.
    </li>
    <li>
      <span class="font-bold text-black">Goal:</span> 
      Significantly improves <b>exploitation capability</b>.
    </li>
  </ul>
</div>

<div>
  <h4 class="text-x font-bold text-yellow-700 mb-3 border-l-4 border-yellow-600 pl-4">
    Onlooker Bees
  </h4>
  <ul class="list-disc list-outside ml-6 space-y-0 text-gray-700 text-m leading-relaxed">
    <li>
      <span class="font-bold text-black">Mechanism:</span> 
      <strong>Spiral Update</strong>.
    </li>
    <li>
      <span class="font-bold text-black">Effect:</span> 
      Bees fly around the optimal solution in a spiral path.
    </li>
    <li>
      <span class="font-bold text-black">Goal:</span> 
      Balances <b>exploration and exploitation</b>.
    </li>
  </ul>
</div>

</div>

::right::

<div class="flex flex-col items-center justify-center h-full ml-8">
  <div class="border-2 border-dashed border-gray-400 rounded-lg p-4 w-full h-80 flex items-center justify-center bg-gray-50">
    <img 
      src="./assets/fig4.png" 
      class="max-h-full max-w-full object-contain" 
      alt="Fig. 4. Schematic diagram of the shrinking encircling mechanism"
    />
  </div>
</div>

---
layout: two-cols
---

# Improvement 3: Path Optimization

### Further Reducing Turn Times

<div class="mt-4 space-y-4">

<div>
  <h4 class="text-lg font-bold text-blue-800 mb-1 border-l-4 border-blue-600 pl-3">
    Principle
  </h4>
  <p class="text-gray-700 text-base leading-snug">
    Check nodes on the path. If two non-adjacent nodes can be directly connected (without obstacles), remove the intermediate nodes.
  </p>
</div>

<div>
  <h4 class="text-lg font-bold text-green-800 mb-1 border-l-4 border-green-600 pl-3">
    Effect
  </h4>
  <p class="text-gray-700 text-base leading-snug">
    Significantly reduces the number of <b>turn times</b> and shortens the path length.
  </p>
</div>

</div>

::right::

<div class="flex flex-col items-center justify-center h-full ml-6">
  <div class="border-2 border-dashed border-gray-400 rounded-lg p-2 w-full h-60 flex items-center justify-center bg-gray-50">
    <img 
      src="./assets/fig6.png" 
      class="max-h-full max-w-full object-contain" 
      alt="Fig. 6. Path optimization mechanism"
    />
  </div>
</div>

---
layout: default
---

# Algorithm Execution Logic

### Complete Process Overview

<div class="w-full max-w-4xl mx-auto mt-8 flex flex-col gap-2">

<div class="flex items-center bg-gray-50 rounded border-l-4 border-gray-400 p-1.5 shadow-sm">
  <div class="flex-shrink-0 w-6 h-6 rounded-full bg-gray-200 text-gray-700 flex items-center justify-center font-bold text-xs mr-3">1</div>
  <div class="text-xs text-gray-800">
    <span class="font-bold mr-1">Initialization:</span>
    <span class="text-gray-600">Initialize algorithm parameters and establish the grid environment model.</span>
  </div>
</div>

<div class="flex justify-start ml-2.5 -my-1 text-gray-300 text-[10px]">↓</div>

<div class="flex items-center bg-yellow-50 rounded border-l-4 border-yellow-400 p-1.5 shadow-sm">
  <div class="flex-shrink-0 w-6 h-6 rounded-full bg-yellow-100 text-yellow-700 flex items-center justify-center font-bold text-xs mr-3">2</div>
  <div class="text-xs text-gray-800">
    <span class="font-bold mr-1">ABC Phase:</span>
    <span class="text-gray-600">Employed, Onlooker, and Scout Bees update path nodes to determine direction.</span>
  </div>
</div>

<div class="flex justify-start ml-2.5 -my-1 text-gray-300 text-[10px]">↓</div>

<div class="flex items-center bg-blue-50 rounded border-l-4 border-blue-500 p-1.5 shadow-sm">
  <div class="flex-shrink-0 w-6 h-6 rounded-full bg-blue-100 text-blue-700 flex items-center justify-center font-bold text-xs mr-3">3</div>
  <div class="text-xs text-gray-800">
    <span class="font-bold mr-1">ACO Phase:</span>
    <span class="text-gray-600">Call <code>Createpath</code> (embedding ACO) to generate paths and calculate fitness.</span>
  </div>
</div>

<div class="flex justify-start ml-2.5 -my-1 text-gray-300 text-[10px]">↓</div>

<div class="flex items-center bg-green-50 rounded border-l-4 border-green-500 p-1.5 shadow-sm">
  <div class="flex-shrink-0 w-6 h-6 rounded-full bg-green-100 text-green-700 flex items-center justify-center font-bold text-xs mr-3">4</div>
  <div class="text-xs text-gray-800">
    <span class="font-bold mr-1">Output:</span>
    <span class="text-gray-600">Check termination conditions. If met, output the <b>Global Optimal Path</b>.</span>
  </div>
</div>

</div>