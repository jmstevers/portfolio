<script lang="ts">
  export let title: string;
  export let category: string;
  export let date: string;
</script>

<a class="pointer-events-auto relative h-min w-full max-w-sm p-4" href="/">
  <div class="absolute bottom-0 left-0 right-0 top-0 -z-10 bg-black blur" />
  <div class="text-white">
    <h1 class="text-6xl">{title}</h1>
    <div>
      <p class="float-left text-xl uppercase">{category}</p>
      <p class="float-right text-xl">{date}</p>
    </div>
  </div>
</a>
