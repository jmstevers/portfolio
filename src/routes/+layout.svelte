<script lang="ts">
  import { fade } from "svelte/transition";
  import Cursor from "../components/Cursor.svelte";
  import "../globals.css";
  import { page } from "$app/stores";
  import { quintInOut } from "svelte/easing";
  import { injectSpeedInsights } from "@vercel/speed-insights/sveltekit";

  injectSpeedInsights();

  let backgroundColor = 217;

  const wrap = (num: number, min: number, max: number) => ((num - min) % (max - min)) + min;

  function handleNavigate(path: string) {
    switch (path) {
      case "/":
        backgroundColor = wrap(217, 0, 360);
        break;
      case "/about":
        backgroundColor = wrap(217 + 90, 0, 360);
        break;
      case "/blog":
        backgroundColor = wrap(217 + 90 * 2, 0, 360);
        break;
      case "/contact":
        backgroundColor = wrap(217 + 90 * 3, 0, 360);
        break;
      default:
        backgroundColor = wrap(217, 0, 360);
        break;
    }
  }

  $: handleNavigate($page.url.pathname);
</script>

<svelte:head>
  <title>jmstevers</title>
  <meta name="description" content="Johnathan Stevers' portfolio website." />
</svelte:head>

<Cursor />

<navbar class="fixed w-full whitespace-nowrap text-2xl text-white">
  <a
    href="/"
    class="absolute transition-transform hover:translate-x-2 {$page.url.pathname === '/'
      ? 'underline'
      : ''}"
  >
    jmstevers
  </a>
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

<div class="absolute -z-50 h-screen w-screen bg-[url(/bg.webp)] bg-no-repeat" />
{#key backgroundColor}
  <div
    class="absolute -z-40 h-full w-full mix-blend-difference"
    style="background-color: hsl({backgroundColor}, 91%, 60%)"
    transition:fade={{ duration: 1000, easing: quintInOut }}
  />
{/key}

<slot />
