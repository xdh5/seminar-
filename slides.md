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

## The Maximum Flow Problem

<div class="mt-12 py-1" hover:bg="white op-10">
  Zhao Zhiyu
</div>

---
---

# Case Study: Seervada Park

<div class="leading-relaxed">


-  **Scenario** The park needs to schedule scenic tram rides.

-  **Goal** Transport the **maximum** number of tourists daily during peak season.

-  **Route** **Entrance (Node O)** $\to$ **Scenic Wonder (Node T)**.

-  **Constraints** Strict upper limits on tram trips per road to protect ecology (Arc Capacity).

<br>

<div class="bg-blue-100 dark:bg-blue-900 p-4 rounded-lg border-l-4 border-blue-500">

How to arrange the routes to maximize the total number of trips?

</div>


</div>


---
layout: two-cols
---

# Building the Network Model

<div class="text-sm leading-snug mt-4 text-gray-700">

**Nodes (Stations)**
<ul class="pl-4 mt-1 mb-4 space-y-1">
  <li><strong>O</strong>: Origin / Entrance (Source)</li>
  <li><strong>T</strong>: Destination (Sink)</li>
  <li><strong>A, B, C, D, E</strong>: Transshipment Nodes</li>
</ul>

**Arcs (Arrows)**
<ul class="pl-4 mt-1 mb-4 space-y-1">
  <li>Represent the direction of the roads.</li>
</ul>

**Numbers**
<ul class="pl-4 mt-1 space-y-1">
  <li>Represent <strong>Capacity</strong> (Maximum trips per day).</li>
</ul>

</div>

::right::

<div class="h-full flex flex-col items-center justify-center p-4">
  
  <!-- Replace with your actual image path -->
  <div class="w-full aspect-video bg-gray-100 border border-gray-300 rounded flex items-center justify-center text-gray-400 text-xs">
      <img 
    src="./assets/residual-network.png" 
    class="rounded-lg shadow-lg object-contain max-h-80 w-auto border-2 border-gray-200"
    alt="Residual Network Diagram"
  />
  </div>


</div>

---
layout: default
---

# The Augmenting Path Algorithm

<div class="text-base leading-relaxed mt-4 text-gray-800">

### Core Iterative Logic for Maximum Flow

<ul class="pl-6 mt-3 space-y-4 list-decimal">
  <li>
    Find any path from O to T in the Residual Network where every arc still has a capacity greater than zero.
  </li>
  <li>
    Calculate The amount of flow we can add is the bottlenec of this path
  </li>
  <li>
    Update Capacities:
    <ul class="pl-6 mt-2 space-y-2 list-disc text-sm">
      <li>Forward Arcs: Decrease residual capacity.</li>
      <li>Reverse Arcs: Increase residual capacity.</li>
    </ul>
  </li>
  <li>
    Continue the process until no Augmenting Path from O to T can be found. The total flow accumulated is the maximum possible flow.
  </li>
</ul>

</div>

---
layout: two-cols
---

# The Residual Network

<div class="mt-8 text-sm text-gray-700 leading-relaxed">

To avoid suboptimal paths, we utilize the **Residual Network**.

<br>

**Key Features**

<ul class="pl-5 mt-2 space-y-4 list-disc">
  <li>
    <strong>Displays Remaining Capacity</strong>
    <br>
    Clearly indicates the specific amount of capacity still available for use on each arc.
  </li>
  <li>
    <strong>Backtracking Mechanism (Reverse Flow)</strong>
    <br>
    Allows for "correction"，undoing previous allocations.
    <br>
  </li>
</ul>

</div>

---
layout: two-cols
---

# Max-Flow Min-Cut Theorem

<div class="mt-8 text-sm text-gray-700 leading-normal">

### Optimality Verification

<ul class="pl-4 mt-2 space-y-3 list-disc">
  <li>
    <strong>Minimum Cut:</strong>
    <br>
    The smallest total capacity of any set of arcs that, if removed, completely disconnects the O from the T.
  </li>
  <li>
    <strong>Theorem:</strong>
    <br>
    The maximum feasible flow is equal to the minimum cut value across the network.
  </li>
  <li>
    <strong>Result Validation:</strong>
    <br>
    The critical cut in the figure has a capacity sum of: 3 + 4 + 1 + 6 = 14.
    <br>
    Since max =14, the theorem confirms the solution is optimal.
  </li>
</ul>

</div>

::right::

<div class="h-full flex flex-col items-center justify-center p-6">
  
  <!-- Image Placeholder for the Min-Cut Diagram -->
  <div class="w-full aspect-video bg-gray-50 border-2 border-dashed border-red-400 rounded-lg flex flex-col items-center justify-center text-gray-400">
  <img 
    src="./assets/min-cut.png" 
    class="rounded-lg shadow-lg object-contain max-h-80 w-auto border-2 border-gray-200"
    alt="Minimum Cut Diagram"
  />
  </div>

</div>