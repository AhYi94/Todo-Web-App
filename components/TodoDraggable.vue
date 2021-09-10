<template>
  <div class="w-1/5">
    <div class="bg-gray-500 p-4 flex justify-between">
      <h1 class="text-white text-2xl self-center">{{ title }}</h1>
      <div class="shadow-inner text-center p-2 bg-white">
        <b>{{ countListItem }}</b> <br />Projects
      </div>
    </div>
    <draggable :list="list" group="task">
      <div
        v-for="element in list"
        :key="element.name"
        class="bg-white p-5 border-b-2 break-all"
      >
        {{ element.name }}
      </div>
    </draggable>
  </div>
</template>
<script>
import draggable from 'vuedraggable'
export default {
  components: {
    draggable,
  },
  props: {
    title: { type: String, default: '' },
    list: {
      type: Array,
      default() {
        return []
      },
    },
  },
  computed: {
    countListItem() {
      return this.list.length
    },
  },
}
</script>
