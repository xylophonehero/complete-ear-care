<script context="module" lang="ts">
  import type { Load } from "@sveltejs/kit"
  import {
    useStoryblokApi,
    StoryblokComponent,
  } from "@storyblok/svelte"

  export const load: Load = async ({ params }) => {
    const storyblokApi = useStoryblokApi()
    const slug = params.slug || "home"
    const { data } = await storyblokApi.get("cdn/stories/" + slug, {
      version: "draft",
    })
    return {
      props: { story: data.story },
    }
  }
</script>

<script>
  export let story
</script>

<div>
  {#if story}
    <StoryblokComponent blok={story.content} />
  {/if}
</div>
