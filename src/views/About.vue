<template>
  <div class="about">
    <chatRoom />
    <router-view />
  </div>
</template>

<script>
// @ is an alias to /src
import chatRoom from "@/components/chatRoom.vue"

export default {
  components: {
    chatRoom,
  },
}
</script>
