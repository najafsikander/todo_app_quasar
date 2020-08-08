<template>
  <q-page class="bg-grey-3 column">
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
          <q-btn @click.stop="deleteTask(index)" flat round color="primary" dense icon="delete" />
        </q-item-section>
      </q-item>
    </q-list>
  </q-page>
</template>

<script>
export default {
  data () {
    return {
      tasks: [
        {
          title: 'Start the Project',
          done: false
        },
        {
          title: 'Work on Project',
          done: true
        },
        {
          title: 'Complete the Project',
          done: false
        }
      ]
    }
  },
  methods: {
    deleteTask(index) {
      
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
</style>
