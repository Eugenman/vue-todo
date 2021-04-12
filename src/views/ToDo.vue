<template lang="pug">
  v-card
    v-col(
      class="mb-5"
    )
      v-text-field(
        v-model="name"
        max-width="300"
        placeholder="Type and press Enter"
        @keypress.enter="name ? addItem() : null"
      )
      v-text-field(
        v-model="count"
        max-width="300"
        placeholder="Type count"
        @keypress.enter="count ? addItem() : null"
      )
      v-btn(
        :disabled="name === ''"
        @click="addItem()"
      ) Добавить
    ToDoList(
      :list="list"
      fixed-header
    )
      template(v-slot:remove="{ index }")
        v-btn(
          class="mx-2"
          dark
          small
          color="primary"
          @click="removeItem(index)"
        )
          v-icon(dark) mdi-minus
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import ToDoList from '@/components/ToDoList.vue';

@Component({
  components: { ToDoList },
})
export default class ToDo extends Vue {
  name = ''

  count = ''

  list = [
    { name: 'Молоко', count: '1' },
    { name: 'Хлеб', count: '2' },
    { name: 'Трюфель', count: '3' },
  ]

  removeItem(idx: number): void {
    this.list.splice(idx, 1);
  }

  addItem(): void {
    this.list.push({ name: this.name ? this.name : '--', count: this.count ? this.count : '--' });
    this.name = '';
    this.count = '';
  }
}
</script>
