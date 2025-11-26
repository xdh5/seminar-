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
layout: two-cols
---

# Problem Context & Goal

<div class="text-sm">

**The Scenario: Seervada Park**
* **Background:** Park management needs to route tram trips during the peak season.
* **The Goal:** Maximize the number of tram trips per day from the **Park Entrance (Station O)** to the **Scenic Wonder (Station T)**.
* **The Constraint:** To protect the local ecology and wildlife, there are strict upper limits (capacities) on the number of trips allowed on each specific road.

**Key Network Definitions:**
* **Source (Node O):** Where all flow originates (The Entrance).
* **Sink (Node T):** Where all flow terminates (The Scenic Wonder).
* **Capacity:** The number on each arrow indicating the max flow limit for that road.

</div>

::right::

<div class="ml-4 h-full flex flex-col justify-center items-center">
  
  <img 
    src="./assets/9ca45dbb-bc36-4359-9201-e2538d9d8992.png" 
    class="rounded-lg shadow-lg object-contain max-h-80 w-auto border-2 border-gray-200"
    alt="Seervada Park Network Diagram"
  />
</div>

---
layout: two-cols
---

# Solution Logic: Residual Network

<div class="text-sm">

**The Augmenting Path Algorithm**
* **Core Logic:** Repeatedly identify directed paths from source to sink with strictly positive residual capacity until no such path exists.

**Two Key Concepts:**
* **Residual Capacity:** How much more flow can fit? (Calculated as: Original Capacity - Used Flow).
* **Back-flow ("Regret Mechanism"):** The algorithm adds a "reverse" arc. If 5 units are assigned forward, the reverse capacity becomes 5.

**Why "Back-flow"?**
* **Function:** It permits the "cancellation" of previously assigned flows to reroute traffic, ensuring the global optimal solution is reached.

</div>

::right::

<div class="ml-4 h-full flex flex-col justify-center items-center">
  
  <img 
    src="./assets/residual-network.png" 
    class="rounded-lg shadow-lg object-contain max-h-80 w-auto border-2 border-gray-200"
    alt="Residual Network Diagram"
  />
</div>

---
layout: two-cols
---

# Iteration Process: Finding Augmenting Paths

<div class="text-sm leading-snug -mt-4">

**Iteration 1:**
* **Path:** $O \rightarrow B \rightarrow E \rightarrow T$
* **Bottleneck:** $\min\{7, 5, 6\} = 5$
* **Action:** Send **5 units**; update residuals.

<div class="my-2"></div>

**Iteration 2:**
* **Path:** $O \rightarrow A \rightarrow D \rightarrow T$
* **Bottleneck:** $\min\{5, 3, 9\} = 3$
* **Action:** Send **3 units**.

<div class="my-2"></div>

**Subsequent Iterations:**
* **Logic:** Continue searching using **"reverse arcs"** (back-flow) until no path to Node T remains.

</div>

::right::

<div class="ml-4 h-full flex flex-col justify-center items-center">
  
  <img 
    src="./assets/iteration-diagram.png" 
    class="rounded-lg shadow-lg object-contain max-h-80 w-auto border-2 border-gray-200"
    alt="Iteration Process Diagram"
  />

</div>

---
layout: two-cols
---

## Optimality Proof: Max-Flow Min-Cut Theorem

<div class="text-xs leading-tight mt-2 mb-2">

* Is our result (14 trips) truly the absolute maximum?

<div class="my-2"></div>

**Key Concepts:**
* **The Cut:** Imagine drawing a line through the network that completely separates the Source (O) from the Sink (T).
* **Cut Value:** The sum of the capacities of all the arcs cut by this line (in the forward direction).

<div class="my-2"></div>

**Max-Flow Min-Cut Theorem:**
* **Theorem:** Maximum Flow = Minimum Cut Value.
* **Meaning:** The network's "tightest bottleneck" determines the maximum possible flow.

<div class="my-2"></div>

**Verification:**
* In this case, we can find a specific cut (severing arcs like $A \rightarrow D$, $B \rightarrow D$, etc.) where the sum of capacities is exactly **14**.
* Since Flow (14) = Cut (14), the solution is optimal.

</div>

::right::

<div class="ml-4 h-full flex flex-col justify-center items-center">
  
  <img 
    src="./assets/min-cut.png" 
    class="rounded-lg shadow-lg object-contain max-h-80 w-auto border-2 border-gray-200"
    alt="Minimum Cut Diagram"
  />

</div>

---
# Default single column layout
---

# Optimal Solution & Applications

<div class="mt-4 text-base leading-normal max-w-4xl">

**The Final Result (Optimal Solution):**
* **Total Max Flow:** **14 trips/day**.
* **Path Allocation:**
  * Arc $O \rightarrow B$: Full capacity (7).
  * Arc $O \rightarrow C$: Full capacity (4).

<div class="my-6"></div>

**Real-World Applications:**
* **Oil Pipelines:** Maximizing the flow of crude oil through a pipeline network.
* **Supply Chains:** Optimizing distribution from factories to customers.
* **Transportation:** Evaluating vehicle throughput capabilities in city grids.

<div class="my-6"></div>

By converting physical networks into mathematical models, we can identify **bottlenecks** (Min-Cut) and squeeze out **every bit of potential** (Max-Flow).

</div>