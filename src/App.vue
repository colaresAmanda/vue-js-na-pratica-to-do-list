<script>
export default {
  data() {
    return {
      tasks: [
        { id: 1, name: 'Learn vue' },
        { id: 2, name: 'Learn npm' },
        { id: 3, name: 'Learn sass' },
      ],
      inputTask: '',
    }
  },
  methods: {
    addTask() {
      if (this.inputTask.trim() != '') {
        this.tasks.push({
          name: this.inputTask,
          id: this.tasks.length + 1
        })
        this.inputTask = ''
      }
    },
    removeTask(id) {
      for (var i = this.tasks.length; i--;) {
        if (this.tasks[i].id === id) {
          this.tasks.splice(i, 1)
        }
      }
    }
  },

}
</script>
<template>
  <main class="w-75 mt-5" id="todo-list">
    <h1 class="text-center mb-5 display-6 fw-bold">TO-DO LIST</h1>
    <form @submit.prevent="addTask" class="d-flex gap-2">
      <input class="form-control" v-model="inputTask" type="text" placeholder="Add a task">
      <button class="btn btn-success">
        Adicionar
      </button>
    </form>
    <br />
    <table class="row">
      <thead class="mb-2">
        <tr class="fw-bold">Task Name</tr>
        <tr></tr>
      </thead>
      <tbody>
        <tr class="d-flex justify-content-between" v-for="task in tasks" :key="task.id">
          <td>
            {{ task.name }}
          </td>
          <td>
            <button class="btn btn-danger" @click="removeTask(task.id)">
              x
            </button>
          </td>
        </tr>
      </tbody>
    </table>
  </main>
</template>