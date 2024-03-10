<script lang="ts">
  import { quintInOut } from "svelte/easing";
  import { fly } from "svelte/transition";
</script>

<div
  class="flex h-screen w-screen items-center justify-center text-justify"
  in:fly={{ y: "-100%", duration: 1000, easing: quintInOut, delay: 500, opacity: 1 }}
  out:fly={{ y: "100%", duration: 1000, easing: quintInOut, opacity: 1 }}
>
  <p class=" mx-32 max-w-4xl text-2xl text-white">
    Hello. My name is Johnathan Stevers. I live in Oklahoma. I am pursuing an associate’s in
    Computer Science at Tulsa Community College. After my associate’s, I plan to attend the
    University of Oklahoma Polytechnic Institute and attain a bachelor's in Artificial Intelligence
    and Advanced Computing. I am interested in web development and applications of artificial
    intelligence in robotics. I am also a Co-Founder of a rural tech startup “Paperlite Software”
    where I develop the websites for our products. I enjoy music, music production, and reading. I
    am currently reading “Thus Spoke Zarathustra” by Friedrich Nietzsche. My current favorite album
    is “graffiti: a mix by roy blair” by Roy Blair. Thank you.
  </p>
</div>
