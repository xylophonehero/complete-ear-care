<script context="module">
  import { storyblokInit, apiPlugin, useStoryblokApi } from "@storyblok/svelte"
  import Page from "../components/Page.svelte"
  import Teaser from "../components/Teaser.svelte"
  import Grid from "../components/Grid.svelte"
  import Feature from "../components/Feature.svelte"
  import Header from "../components/layout/Header.svelte"
  storyblokInit({
    accessToken: import.meta.env.VITE_STORYBLOK_ACCESS_TOKEN,
    use: [apiPlugin],
    components: {
      page: Page,
      teaser: Teaser,
      grid: Grid,
      feature: Feature,
    },
  })

  export async function load() {
    const storyblokApi = useStoryblokApi()
    const { data } = await storyblokApi.get("cdn/stories/layout/header", {
      version: "draft",
    })
    return {
      props: { story: data.story },
    }
  }
</script>

<script>
  import "../app.css"
  export let story
</script>

<Header blok={story.content} />
<main>
  <slot />
</main>
