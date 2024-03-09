<script lang="ts">
  import { onMount } from "svelte";

  let cursorX = 0;
  let cursorY = 0;
  let mouseX = 0;
  let mouseY = 0;

  let cursor: HTMLElement | null = null;

  onMount(() => {
    cursor = document.getElementById("cursor");
    window.addEventListener("mousemove", handleMouseMove);
    requestAnimationFrame(updateCursor);
  });

  function handleMouseMove(event: MouseEvent) {
    mouseX = event.clientX - cursor?.offsetWidth! / 2;
    mouseY = event.clientY - cursor?.offsetHeight! / 2;
  }

  function updateCursor() {
    cursorX += (mouseX - cursorX) * 0.05;
    cursorY += (mouseY - cursorY) * 0.05;

    if (cursorX + cursor!.offsetWidth > window.innerWidth) {
      cursorX = window.innerWidth - cursor!.offsetWidth;
    }

    if (cursorY + cursor!.offsetHeight > window.innerHeight) {
      cursorY = window.innerHeight - cursor!.offsetHeight;
    }

    if (cursorX < 0) {
      cursorX = 0;
    }

    if (cursorY < 0) {
      cursorY = 0;
    }

    cursor!.style.left = `${cursorX}px`;
    cursor!.style.top = `${cursorY}px`;

    requestAnimationFrame(updateCursor);
  }
</script>

<div
  id="cursor"
  class="absolute w-24 h-24 rounded-full bg-white mix-blend-difference z-50 pointer-events-none"
/>
