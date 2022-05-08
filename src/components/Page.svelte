<script>
  import { storyblokEditable , StoryblokComponent} from "@storyblok/svelte";
  export let blok;
</script>

{#each blok.body as item}
<StoryblokComponent blok={item} />
{/each}