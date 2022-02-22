<script lang="ts">
  import "twind/shim"
  import { tw } from "twind"

  import Head from "./lib/Head.svelte"
  import { Twitter } from "svelte-share-buttons-component"

  const url = "https://single-page-svelte.vercel.app"
  const title = "ประกาศยัง?!"

  const description = "ประกาศยัง?!"
  const imageUrl =
    "https://raw.githubusercontent.com/narze/timelapse/master/projects/single-page-svelte_home.png"
  const gtagId = null

  import { onMount } from "svelte"

  let time = new Date()

  // these automatically update when `time`
  // changes, because of the `$:` prefix
  $: hours = time.getHours()
  $: minutes = time.getMinutes() < 10 ? "0" + time.getMinutes() : time.getMinutes()
  $: seconds = time.getSeconds()

  onMount(() => {
    const interval = setInterval(() => {
      time = new Date()
    }, 1000)

    return () => {
      clearInterval(interval)
    }
  })
</script>

<Head {title} {description} {url} {imageUrl} {gtagId} />

<main class="w-full h-screen flex flex-col justify-center items-center font-sans">
  <h1 class="text-6xl  flex flex-col mb-10">
    {`${hours}:${minutes.toLocaleString()} ประกาศยัง?!`}
  </h1>
  <div class="flex justify-center items-center space-x-4 ">
    <div class="flex flex-col justify-center items-center">
      <Twitter class="h-10 w-10" text={`${hours}:${minutes} ยังไม่ประกาศ`} url={""} />
      <p class="text-black">ยังไม่ประกาศ</p>
    </div>
    <div class="flex flex-col justify-center items-center">
      <Twitter class="h-10 w-10" text={`${hours}:${minutes} ประกาศแล้ว`} url={""} />
      <p class="text-black">ประกาศแล้ว</p>
    </div>
  </div>
</main>

<style>
  :root {
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen, Ubuntu, Cantarell,
      "Open Sans", "Helvetica Neue", sans-serif;
  }
</style>
