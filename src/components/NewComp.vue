    
<template>
  <div>
    <slot name="username"></slot>
    <slot></slot>
    <slot name="exit"></slot>
  </div>
</template>

<script>
export default {
    props : ['users']
}
</script>

<style>

</style>
