<template lang="pug">
  v-card
    v-col(
      class="mb-5"
    )
      v-text-field(
        v-model="name"
        max-width="300"
        placeholder="Введите имя и нажмите Enter"
        @keypress.enter="name ? addItem() : null"
      )
      v-text-field(
        v-model="count"
        max-width="300"
        placeholder="Введите количество"
        @keypress.enter="count && name ? addItem() : null"
      )
      v-btn(
        :disabled="name === ''"
        @click="addItem()"
      ) Добавить
    ToDoList(
      :list="list"
      fixed-header
      v-slot:remove="{ index }"
    )
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
    { name: 'Молоко', count: '3' },
    { name: 'Хлеб', count: '6' },
    { name: 'Трюфель', count: '5' },
  ]

  removeItem(index: number): void {
    this.list.splice(index, 1);
  }

  addItem(): void {
    this.list.push({ name: this.name, count: this.count ? this.count : '--' });
    this.name = '';
    this.count = '';
  }
}
</script>
