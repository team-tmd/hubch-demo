<template>
  <div class="home">
    <SignUp />
    <router-view />
  </div>
</template>

<script>
// @ is an alias to /src
import SignUp from "@/components/SignUp.vue"

export default {
  components: {
    SignUp,
  },
}
</script>
