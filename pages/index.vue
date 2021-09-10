<template>
  <div class="mx-20">
    <div class="flex justify-between my-5">
      <div class="my-5 w-1/3">
        <div class="flex">
          <input
            v-model="newItem.name"
            class="
              shadow
              appearance-none
              border
              rounded
              w-full
              py-2
              px-3
              text-gray-700
              leading-tight
              focus:outline-none focus:shadow-outline
            "
          />
          <button
            class="
              bg-green-500
              hover:bg-green-700
              text-white
              font-bold
              w-1/4
              py-1
              px-1
              ml-5
              rounded
            "
            @click="addItem"
          >
            Add Project
          </button>
        </div>
      </div>

      <div>
        <div class="ml-auto text-center">
          <label class="uppercase font-bold"> Total </label>
          <div class="shadow-inner text-center p-2 bg-white">
            <b>{{ totalItems }}</b> <br />Projects
          </div>
        </div>
      </div>
    </div>
    <div class="flex justify-between">
      <todo-draggable title="To Do" :list="todo" />
      <todo-draggable title="In Progress" :list="inProgress" />
      <todo-draggable title="Done" :list="done" />
    </div>
  </div>
</template>

<script>
import TodoDraggable from '~/components/TodoDraggable.vue'
export default {
  components: { TodoDraggable },
  data() {
    return {
      todo: [
        { name: 'Project 1', id: 1 },
        { name: 'Project 2', id: 2 },
        { name: 'Project 3', id: 3 },
        { name: 'Project 4', id: 4 },
      ],
      inProgress: [
        { name: 'Project 5', id: 1 },
        { name: 'Project 6', id: 2 },
      ],
      done: [
        { name: 'Project 7', id: 1 },
        { name: 'Project 8', id: 2 },
        { name: 'Project 9', id: 2 },
      ],
      newItem: { name: null, id: null, list: null },
    }
  },
  computed: {
    totalItems() {
      const totalProject =
        this.todo.length + this.inProgress.length + this.done.length
      return totalProject
    },
  },
  methods: {
    addItem() {
      if (!this.newItem.name) {
        alert("Title shouldn't be empty")
        return
      }
      this.newItem.id = this.todo.length + 1
      this.newItem.todo = 1
      this.todo.push({ ...this.newItem })
      this.newItem.name = null
    },
  },
}
</script>
