<script>
  export let title = "Sample title"
  export let content = "Sample content"
  export let type = 'Text'
  export let shapes = 0
  export let colors = ['red', 'yellow', 'blue']

  let baseClass = type.toLowerCase()

  import Blobs from './Blobs.svelte'
</script>

<div class="wrapper">
  <div class="{baseClass}">
    <h2 class="{baseClass}__title">{title}</h2>
    <div class="{baseClass}__content">{@html content}</div>
  </div>
  <Blobs shapes={shapes} colors="{colors}"></Blobs>
</div>