<script>
  export let baseClass
  export let hash
</script>

<div class="{baseClass}__navigation">
  <div class="{baseClass}__prev {baseClass}__prev--{hash}">{'<- Prev'}</div>
  <div class="{baseClass}__prev {baseClass}__next--{hash}">Next -></div>
</div>