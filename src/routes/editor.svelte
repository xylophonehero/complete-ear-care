<script lang="ts" context="module">
  import type { Load } from "@sveltejs/kit"
  import { onMount } from "svelte"
  import {
    useStoryblokBridge,
    StoryblokComponent,
    useStoryblokApi,
  } from "@storyblok/svelte"

  export const load: Load = async ({ url }) => {
    const storyblokApi = useStoryblokApi()
    const { data } = await storyblokApi.get(
      "cdn/stories/" + url.searchParams.get("slug"),
      {
        version: "draft",
      }
    )
    return {
      props: { story: data.story },
    }
  }
</script>

<script>
  export let story

  onMount(() => {
    useStoryblokBridge(story.id, (newStory) => (story = newStory))
  })
</script>

{#if story}
  <StoryblokComponent blok={story.content} />
{/if}
