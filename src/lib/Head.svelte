<script lang="ts">
  export let title: string
  export let description: string
  export let url: string
</script>

<svelte:head>
  <title>{title}</title>

  <meta name="title" content={title} />
  <meta name="description" content={description} />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <meta property="og:url" content={url} />
  <meta property="og:type" content="website" />
  <meta property="og:title" content={title} />
  <meta property="og:description" content={description} />

  <meta name="twitter:title" content={title} />
  <meta name="twitter:card" content="summary_large_image" />
</svelte:head>
