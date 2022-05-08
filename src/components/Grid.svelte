<script>
  import { storyblokEditable, StoryblokComponent } from "@storyblok/svelte";
  export let blok;
</script>

<div use:storyblokEditable={blok}>
{#each blok.columns as column}
  <StoryblokComponent blok={column} />
{/each}
</div>