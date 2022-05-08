<script lang="ts">
  import Image from "$lib/atoms/Image.svelte"
  import Link from "$lib/atoms/Link.svelte"

  import { storyblokEditable } from "@storyblok/svelte"
  import type { HeaderStoryblok } from "component-types-sb"
  export let blok: HeaderStoryblok
  console.log(blok)
</script>

<div use:storyblokEditable={blok}>
  <div class="wrapper container">
    <Image image={blok.logo} />
  </div>
  <div class="nav-wrapper">
    <nav class="container">
      <ul>
        {#each blok.nav as item}
          <li>
            <Link link={item.link[0]} />
            {#if item.dropdownLinks && item.dropdownLinks.length > 0}
              <ul>
                {#each item.dropdownLinks as link}
                  <li>
                    <Link {link} />
                  </li>
                {/each}
              </ul>
            {/if}
          </li>
        {/each}
        <li />
      </ul>
    </nav>
  </div>
</div>

<style>
  .wrapper {
    color: var(--brand);
  }

  .nav-wrapper {
    background-color: var(--blue-6);
    color: var(--red-7);
  }
  nav {
    display: flex;
  }
</style>
