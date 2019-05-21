<template>
  <div class="about">
    <h1>This is a page about {{myname}}</h1>
    <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna ali...</p>
  </div>
</template>

<script>
export default {
  name: 'About',
  data() {
    return {
      myname: this.$route.params.myname
    }
  }
}
</script>
