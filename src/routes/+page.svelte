<script>
  import { quintOut } from "svelte/easing";
  import { fly } from "svelte/transition";
</script>

<div
  class="fixed bottom-0 flex w-screen justify-between text-2xl text-white sm:text-4xl md:text-5xl lg:text-7xl xl:text-7xl 2xl:text-8xl"
  in:fly={{ x: -2000, duration: 1000, easing: quintOut, delay: 500 }}
  out:fly={{ x: 2000, duration: 1000, easing: quintOut }}
>
  <a href="/" class="transition-transform hover:-translate-y-5">WEB</a>
  <a href="/" class="transition-transform hover:-translate-y-5">AI</a>
  <a href="/" class="transition-transform hover:-translate-y-5">ROBOTICS</a>
  <a href="/" class="transition-transform hover:-translate-y-5">STARTUPS</a>
</div>
