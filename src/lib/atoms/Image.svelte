<script lang="ts">
  interface StoryblokImage {
    alt?: string
    copyright?: string
    id: number
    filename: string
    name: string
    title?: string
  }
  export let image: StoryblokImage
  const src = `${image.filename}/m/200x0`
</script>

<img {src} alt={image.alt} />
