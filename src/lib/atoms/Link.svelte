<script lang="ts">
  import type { LinkStoryblok } from "component-types-sb"
  export let link: LinkStoryblok
</script>

{#if link.link.linktype === "story"}
  <a href={"/" + link.link.cached_url}>
    {link.text}
  </a>
{:else if link.link.linktype === "asset" || link.link.linktype === "url"}
  <a href={link.link.cached_url}>
    {link.text}
  </a>
{:else if link.link.linktype === "email"}
  <a href={"mailto:" + link.link.email}>
    {link.text}
  </a>
{/if}
