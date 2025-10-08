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

## Path Planning Technique for Mobile Robots: A Review

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

# Summary: How Robots Find Their Way

<div class="grid grid-cols-2 gap-8">

<div>

### What is this paper about?
This paper is a **review**. It gives us a big picture of **robot path planning**. It covers:
* Important tech and main methods.
* What we know now and future problems.

<br>

### What a robot needs before it moves
It needs to understand two things:
1. **The World (Maps)**
2. **What is a "Good" Path?**


</div>

<div>

### Two Main Types of Planning

* **Single-Agent (SAPF):**
  For **one robot** to find its path.

* **Multi-Agent (MAPF):**
  For a **group of robots** to work together and not crash.

<br>

### What's Next? Future Ideas

* **Problems**: How to move in busy or changing places.
* **The Future is AI**: Using **Artificial Intelligence (AI)** is a big new idea.
* **Learning Robots**: AI helps robots learn from what they do, so they can make better choices.

</div>

</div>

<!--
So, let's look at the background for my research.
First, there are lots of robots. Because we all shop online more, companies use more robots in their warehouses to move things quickly.
But there is a problem. These warehouses are very busy and always changing. The robots' plans are too simple, like a basic map. They get confused when something unexpected blocks their way.
This confusion causes them to take long, inefficient trips. This wastes a lot of battery power. With thousands of robots, it's a big waste of electricity and bad for the environment.
So, the goal of my research is to give these robots a smarter brain. A brain that can see the busy environment and make smart decisions. This will help them find the best path, save energy, and create a greener system.
-->

---
# 主題：seriph (這是一個簡潔的主題)
theme: seriph
# 版面：預設
layout: default
---

# The Classic Ways

<div class="grid grid-cols-2 gap-12 pt-4">

<div>
  <h3>📍 Dijkstra's Algorithm</h3>
  <p class="text-lg opacity-60">Slow but Sure</p>

  <div class="mt-4">
    <p><strong>How it works:</strong></p>
    <p>It starts at the beginning and checks <strong>every possible step</strong> outwards, like ripples in water, until it finds the goal.</p>
  </div>

  <div class="mt-4">
    <p>👍 <strong>Good part:</strong></p>
    <p>It <span class="text-green-500 font-bold">always</span> finds the shortest path. No mistakes.</p>
  </div>

  <div class="mt-4">
    <p>👎 <strong>Bad part:</strong></p>
    <p>It can be very slow because it checks too many useless places.</p>
  </div>
</div>

<div>
  <h3>⭐ A* (A-Star) Algorithm</h3>
  <p class="text-lg opacity-60">Smart and Fast</p>

  <div class="mt-4">
    <p><strong>How it works:</strong></p>
    <p>A smarter version of Dijkstra. It uses a clever <strong>"guess"</strong> to decide which way is closer to the goal. It doesn't waste time.</p>
  </div>

  <div class="mt-4">
    <p class="text-xs mt-1">Total Score = <span class="text-blue-500">Distance from Start</span> + <span class="text-orange-500">Guessed Distance to Goal</span></p>
  </div>

  <div class="mt-4">
    <p>👍<strong>Good part:</strong></p>
    <p>It is much faster, but it <span class="text-green-500 font-bold">also</span> finds the shortest path. A true classic!</p>
  </div>
</div>

</div>

---
theme: seriph
layout: default
---

# The Classic Ways

<div class="grid grid-cols-2 gap-12 pt-4">

<div>
  <div class="mt-6">
    <h4><strong>RRT (Rapidly-exploring Random Tree)</strong></h4>
    <p><strong>How it works:</strong> It "grows" a tree of paths by picking random spots. The tree branches out until one branch hits the goal.</p>
    <p class="mt-2">✨ <strong>RRT* is a better version</strong> that keeps improving the path to make it shorter.</p>
  </div>

  <div class="mt-6">
    <h4><strong>PRM (Probabilistic Roadmap)</strong></h4>
    <p><strong>How it works:</strong> First, it places many random dots on the map. Then, it connects nearby dots to create a "road network". Finally, it finds the best path on these roads.</p>
  </div>
</div>

<div>
  <h4>🧲 Artificial Potential Field (APF)</h4>

  <div class="mt-6">
    <p><strong>How it works:</strong></p>
    <p>Imagine the goal is a <span class="text-blue-500">positive magnet</span> that PULLS the robot. Obstacles are <span class="text-red-500">negative magnets</span> that PUSH it away. The robot just follows the forces!</p>
  </div>

  <div class="mt-6">
    <p>👍 <strong>Good Parts:</strong></p>
    <ul class="list-disc pl-5">
      <li>It is very simple and fast.</li>
      <li>The path it creates is very smooth.</li>
    </ul>
  </div>

  <div class="mt-6">
    <p>👎 <strong>Bad Part:</strong></p>
    <p>The robot can get <strong>stuck</strong> if the push and pull forces become equal. It won't know where to go next.</p>
  </div>
</div>

</div>

---
theme: seriph
layout: default
---

# Intelligent optimization algorithm

<div class="grid grid-cols-2 gap-12 pt-4">

<div>
  <h3>🐜 Ant Colony Optimization (ACO)</h3>
    
  <p class="mt-4"><strong>How it works:</strong></p>
  <p>Many "virtual ants" search for a path. When they find a short path, they leave a strong trail (called a pheromone). Other ants will follow the strongest trail. Soon, all ants use the best path!</p>
  
  <p class="mt-4"><strong>Good Part:</strong></p>
  <p>It's a very strong and reliable method.</p>
</div>

<div>
  <h3>🐦 Particle Swarm Optimization (PSO)</h3>
    
  <p class="mt-4"><strong>How it works:</strong></p>
  <p>Many "particles" (like birds) fly around. Each particle remembers its own best spot and also knows the best spot the whole group has found. They use this information to fly towards better and better places.</p>
  
  <p class="mt-4"><strong>Good Part:</strong></p>
  <p>It finds a good path by sharing information.</p>
</div>

</div>

---
theme: seriph
layout: default
---

# Intelligent optimization algorithm

### 🧬 Genetic Algorithm (GA)

<p class="mt-4"><strong>How it works:</strong></p>
<p>It "evolves" the best path over many generations, just like in nature!</p>

<div class="mt-6 space-y-4">
  <div class="flex items-start">
    <div class="text-2xl mr-4">1.</div>
    <div>
      <h4 class="font-bold text-green-600">Selection</h4>
      <span>Pick the "fittest" paths (the best ones) to be parents for the next generation.</span>
    </div>
  </div>
  <div class="flex items-start">
    <div class="text-2xl mr-4">2.</div>
    <div>
      <h4 class="font-bold text-blue-600">Crossover</h4>
      <span>Mix parts of two parent paths to create new child paths. This combines good ideas.</span>
    </div>
  </div>
  <div class="flex items-start">
    <div class="text-2xl mr-4">3.</div>
    <div>
      <h4 class="font-bold text-orange-600">Mutation</h4>
      <span>Make a small, random change to a path. This helps discover new, maybe even better, ideas.</span>
    </div>
  </div>
</div>

<p>It's very good at searching everywhere for the best path, but it can be slow.</p>

---
theme: seriph
layout: default
---

# The AI Way

<div class="grid grid-cols-2 gap-12 pt-4">

<div>
  <h3>🧠 Neural Network (NN)</h3>

  <p class="mt-4"><strong>How it works:</strong></p>
  <p>You "teach" the robot by showing it lots of maps and good paths. The robot's brain (the network) learns the rules. After training, it can look at a new map and quickly decide where to go.</p>

  <p class="mt-4"><strong>In short:</strong></p>
  <p>It learns from examples to make fast decisions.</p>
</div>

<div>
  <h3>🎮 Reinforcement Learning (RL)</h3>

  <p class="mt-4"><strong>How it learns:</strong></p>
  <ol class="list-decimal pl-5 space-y-2">
    <li>The robot tries an <strong>Action</strong> (like moving forward).</li>
    <li>The world gives it a <strong>Reward</strong> (a good point for a good move, a bad point for a crash).</li>
    <li>The robot uses the reward to update its plan and make better choices next time.</li>
  </ol>

  <p class="mt-4">✨ <strong>Deep RL (DRL)</strong> is a super-smart version where the robot has a powerful brain (Deep Learning) and learns by trying. It's great for unknown places!</p>
</div>

</div>

---
theme: seriph
layout: default
---

# Comparing The Methods

<!-- Using text-xs for smaller font and gap-4 for less space -->
<div class="grid grid-cols-3 gap-4 pt-2 text-xs">

  <!-- Column 1: Classic Algorithms -->
  <div class="p-3 bg-gray-100 rounded">
    <h3 class="font-bold text-base">Classic Ways</h3>
    <p class="opacity-50">A*, RRT*, APF</p>
    <hr class="my-1">
    <p><strong>Idea:</strong> Uses math and rules.</p>
    <p class="mt-2"><strong>Pros:</strong></p>
    <ul class="list-disc pl-4">
      <li>Reliable, finds the best path.</li>
    </ul>
    <p class="mt-2"><strong>Cons:</strong></p>
    <ul class="list-disc pl-4">
      <li>Needs a perfect map, not flexible.</li>
    </ul>
    <p class="mt-2"><strong>Use:</strong> Known places (indoors, games).</p>
  </div>

  <!-- Column 2: Intelligent Optimization -->
  <div class="p-3 bg-gray-100 rounded">
    <h3 class="font-bold text-base">Intelligent optimization algorithm</h3>
    <p class="opacity-50">ACO, PSO, GA</p>
    <hr class="my-1">
    <p><strong>Idea:</strong> Inspired by nature (ants, birds).</p>
    <p class="mt-2"><strong>Pros:</strong></p>
    <ul class="list-disc pl-4">
      <li>Finds great paths, doesn't get stuck.</li>
    </ul>
    <p class="mt-2"><strong>Cons:</strong></p>
    <ul class="list-disc pl-4">
      <li>Slow, hard to set up.</li>
    </ul>
    <p class="mt-2"><strong>Use:</strong> Complex problems.</p>
  </div>

  <!-- Column 3: Artificial Intelligence -->
  <div class="p-3 bg-gray-100 rounded">
    <h3 class="font-bold text-base">The AI Way</h3>
    <p class="opacity-50">NN, DRL</p>
    <hr class="my-1">
    <p><strong>Idea:</strong> Learns from data and trying.</p>
    <p class="mt-2"><strong>Pros:</strong></p>
    <ul class="list-disc pl-4">
      <li>Adapts to new places, no map needed.</li>
    </ul>
    <p class="mt-2"><strong>Cons:</strong></p>
    <ul class="list-disc pl-4">
      <li>Needs lots of data & power.</li>
    </ul>
    <p class="mt-2"><strong>Use:</strong> Unknown places (outdoors, driving).</p>
  </div>

</div>

<div class="mt-4 text-center text-gray-500 text-sm">
  <strong>Conclusion:</strong> Classic ways are the base, Intelligent optimization algorithm solve tough problems, and AI is the future.
</div>