<template lang="pug">
  v-app
    v-main
      v-container
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
