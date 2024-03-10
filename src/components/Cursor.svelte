<script lang="ts">
  import { onMount } from "svelte";

  let cursorX = 0;
  let cursorY = 0;
  let scale = 1;
  let mouseX = 0;
  let mouseY = 0;

  let cursor: HTMLElement;

  const clamp = (num: number, min: number, max: number) => Math.min(Math.max(num, min), max);

  onMount(() => {
    window.addEventListener("mousemove", handleMouseMove);
    requestAnimationFrame(updateCursor);
  });

  function handleMouseMove(event: MouseEvent) {
    mouseX = event.clientX - cursor.offsetWidth / 2;
    mouseY = event.clientY - cursor.offsetHeight / 2;
  }

  function updateCursor() {
    if (cursorX === mouseX && cursorY === mouseY) {
      requestAnimationFrame(updateCursor);
      return;
    }

    cursorX += (mouseX - cursorX) * 0.05;
    cursorY += (mouseY - cursorY) * 0.05;

    const speed = Math.sqrt((cursorX - mouseX) ** 2 + (cursorY - mouseY) ** 2);

    const newSize = 112 - speed * 0.3;

    const size = clamp(newSize, 20, 112);

    scale += (size / 56 - scale) * 0.05;

    cursor.style.left = `${cursorX}px`;
    cursor.style.top = `${cursorY}px`;
    cursor.style.transform = `scale(${scale})`;

    requestAnimationFrame(updateCursor);
  }
</script>

<div
  bind:this={cursor}
  class="pointer-events-none absolute z-50 h-14 w-14 rounded-full bg-white mix-blend-difference after:rounded-full"
/>
