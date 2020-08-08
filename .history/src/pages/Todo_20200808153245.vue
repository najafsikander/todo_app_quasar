<template>
  <q-page class="bg-grey-3 column">
    <q-list class="bg-white" separator bordered>
      <q-item
      v-for="task in tasks"
      :key="task.title"
       v-ripple>
        <q-item-section avatar>
          <q-checkbox v-model="color" color="primary" />
        </q-item-section>
        <q-item-section>
          <q-item-label>{{ task.title }}</q-item-label>
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
          done: false
        },
        {
          title: 'Complete the Project',
          done: false
        }
      ]
    }
  }
}
</script>
