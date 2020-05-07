<template>
  <div class="moje">
    <img alt="Vue logo" src="../assets/logo.png" />
    <Karty msg="ahoj" msg2="druha zprava" />
  </div>
</template>

<script>
// @ is an alias to /src
import Karty from '@/components/Karty.vue'

export default {
  name: 'moje',
  components: {
    Karty
  }
}
</script>
