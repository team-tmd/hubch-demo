<template>
  <div class="home">
    <homePage />
    <router-view />
  </div>
</template>

<script>
// @ is an alias to /src
import homePage from "@/components/homePage.vue"

export default {
  components: {
    homePage,
  },
}
</script>
