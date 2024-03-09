<script lang="ts">
  import Cursor from "../components/Cursor.svelte";
  import "../globals.css";
  import { page } from "$app/stores";

  let backgroundColor = "bg-blue-500";

  function handleNavigate(path: string) {
    switch (path) {
      case "/":
        backgroundColor = "bg-blue-500";
        break;
      case "/about":
        backgroundColor = "bg-amber-600";
        break;
      case "/blog":
        backgroundColor = "bg-green-500";
        break;
      case "/contact":
        backgroundColor = "bg-fuchsia-600";
        break;
      default:
        backgroundColor = "bg-blue-500";
        break;
    }
  }

  $: handleNavigate($page.url.pathname);
</script>

<Cursor />

<navbar class="fixed z-40 w-full whitespace-nowrap text-2xl text-white">
  <a
    href="/"
    class="absolute transition-transform hover:translate-x-2 {$page.url.pathname === '/'
      ? 'underline'
      : ''}">jmstevers</a
  >
  <div class="float-right flex flex-col space-y-2 text-end">
    <a
      class="transition-transform hover:-translate-x-2 {$page.url.pathname === '/about'
        ? 'underline'
        : ''}"
      href="/about"
    >
      ABOUT
    </a>
    <a
      class="transition-transform hover:-translate-x-2 {$page.url.pathname === '/blog'
        ? 'underline'
        : ''}"
      href="/blog"
    >
      BLOG
    </a>
    <a
      class="transition-transform hover:-translate-x-2 {$page.url.pathname === '/contact'
        ? 'underline'
        : ''}"
      href="/contact"
    >
      CONTACT
    </a>
  </div>
</navbar>

<div
  class="absolute -z-50 h-screen w-screen overflow-x-hidden bg-[url(/background.png)] bg-fixed bg-no-repeat"
/>
<div
  class="absolute -z-40 h-full w-full {backgroundColor} bg-fixed bg-no-repeat mix-blend-difference transition-colors duration-1000"
/>

<main class="overflow-x-hidden">
  <slot />
</main>
