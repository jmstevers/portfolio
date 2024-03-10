<script lang="ts">
  import { quintInOut } from "svelte/easing";
  import { page } from "$app/stores";
  import BlogPost from "../../components/BlogPost.svelte";

  function scaleMask(node: HTMLElement, { delay = 0, duration = 1000, easing = quintInOut }) {
    return {
      duration,
      easing,
      delay,
      opacity: 1,
      css: (t: number) => {
        return `mask-size: ${t * 100}% ${t * 100}%;`;
      },
    };
  }
</script>

<div class="pointer-events-none relative h-screen w-screen overflow-hidden">
  <div
    in:scaleMask={{ delay: 500 }}
    out:scaleMask={{}}
    class="circle-mask relative left-1/2 top-1/2 z-50 h-[120vw] w-[120vw] -translate-x-1/2 -translate-y-1/2 bg-white mix-blend-difference"
  >
    <div
      class="absolute left-1/2 top-1/2 z-10 flex h-screen w-screen -translate-x-1/2 -translate-y-1/2 flex-wrap justify-center gap-16 p-8"
    >
      <BlogPost title="hello" category="robotics" date="3/9/2024" />
      <BlogPost title="My First Post" category="robotics" date="3/9/2024" />
    </div>
  </div>
</div>

<style>
  .circle-mask {
    mask: radial-gradient(circle, black 70%, transparent 0);
    mask-size: 100% 100%;
    mask-repeat: no-repeat;
    mask-position: center;
  }
</style>
