<template lang="pug">
  v-app
    v-main(
      class="grey lighten-5"
    )
      v-container
        v-col(
          sm="4"
          class="mx-auto"
        )
          ToDo
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import ToDo from '@/views/ToDo.vue';

@Component({
  components: { ToDo },
})
export default class App extends Vue {
}
</script>

<style lang="sass">
</style>
