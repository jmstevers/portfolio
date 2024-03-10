<script lang="ts">
  import { quintInOut } from "svelte/easing";
  import { fly } from "svelte/transition";
</script>

<div
  class="fixed bottom-0 flex w-screen justify-between text-2xl text-white sm:text-4xl md:text-5xl lg:text-7xl xl:text-7xl 2xl:text-8xl"
  in:fly={{ x: "-100%", duration: 1000, easing: quintInOut, delay: 500, opacity: 1 }}
  out:fly={{ x: "100%", duration: 1000, easing: quintInOut, opacity: 1 }}
>
  <a href="/projects?q=web" class="transition-transform hover:-translate-y-5">WEB</a>
  <a href="/projects?q=ai" class="transition-transform hover:-translate-y-5">AI</a>
  <a href="/projects?q=robotics" class="transition-transform hover:-translate-y-5">ROBOTICS</a>
  <a href="/projects?q=startups" class="transition-transform hover:-translate-y-5">STARTUPS</a>
</div>
