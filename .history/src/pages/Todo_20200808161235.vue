<template>
  <q-page class="bg-grey-3 column">
    <div class="row q-pa-sm bg-primary">
      <q-input @keyup.enter="addTask" class="col" v-model="newTask" placeholder="Add Task" dense bg-color="white" filled square>
        <template v-slot:append>
          <q-btn @click="addTask" round dense flat icon="add" />
        </template>
      </q-input>
    </div>
    <q-list class="bg-white" separator bordered>
      <q-item
      v-for="(task,index) in tasks"
      :key="task.title"
      clickable
      :class="{ 'done bg-blue-1' : task.done}"
      @click="task.done = !task.done"
       v-ripple>
        <q-item-section avatar>
          <q-checkbox v-model="task.done" color="primary"  class="no-pointer-events"/>
        </q-item-section>
        <q-item-section>
          <q-item-label>{{ task.title }}</q-item-label>
        </q-item-section>
        <q-item-section v-if="task.done" side>
          <q-btn @click.stop="confirm = !confirm" flat round color="primary" dense icon="delete" />
        </q-item-section>
            <q-dialog v-model="confirm" persistent>
      <q-card>
        <q-card-section class="row items-center">
          <q-avatar icon="delete" color="primary" text-color="white" />
          <span class="q-ml-sm">You really want to delete the task?</span>
        </q-card-section>

        <q-card-actions align="right">
          <q-btn flat label="Cancel" color="primary" v-close-popup />
          <q-btn flat label="Yes" color="primary" @click.stop="deleteTask(index)" v-close-popup />
        </q-card-actions>
      </q-card>
    </q-dialog>
      </q-item>
    </q-list>
    <div class="no-task absolute-center">
      <q-icon name="check" size="100px" color="primary"/>
      <div class="text-h5 text-primary text-center">No Tasks</div>
    </div>
  </q-page>
</template>

<script>
export default {
  data () {
    return {
      newTask: '',
      tasks: [

      ],
      confirm: false
    }
  },
  methods: {
    deleteTask (index) {
      this.tasks.splice(index, 1)
      this.confirm = !this.confirm
      this.$q.notify('Task Deleted')
    },
    addTask () {
      this.tasks.push({
        title: this.newTask,
        done: false
      })
      this.newTask = ''
      console.log('Task Added')
    }
  }
}
</script>

<style lang="scss">
  .done{
    .q-item__label
    {
      text-decoration: line-through;
      color: #bbb;
    }
  }
  .no-tasks {
    opacity: 0.5;
  }
</style>
