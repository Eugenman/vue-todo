<template lang="pug">
  v-simple-table(
    v-bind="$attrs"
  )
    thead
      tr
        th Название
        th Количество
        th Количество
    draggable(
      v-if="list.length"
      tag="tbody"
      handle=".handle"
      @start="isDragging = true"
      @end="isDragging = false"
      ghost-class="ghost"
    )
      tr(
        v-for="(element, index) in list"
        :key="`${index}`"
        class="handle"
        :style="isDragging ? { cursor: 'grabbing' } : ''"
      )
        td {{ element.name }}
        td {{ element.count }}
        td
          slot(
            name="remove"
            v-bind:index="index"
          )
    v-container(
      v-else
    )
      div Список пуст
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator';
import draggable from 'vuedraggable';

@Component({ components: { draggable } })
export default class ToDoList extends Vue {
  @Prop({ type: Array }) list!: []

  isDragging = false
}
</script>

<style lang="sass" scoped>
  table tr th
    width: 50%
  .handle
    cursor: pointer
  .grabbing
    cursor: grab
  .ghost
    background: #DEB887FF
</style>
