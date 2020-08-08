<template>
  <q-page class="bg-grey-3 column">
    <q-list>
      <!--
        Rendering a <label> tag (notice tag="label")
        so QCheckboxes will respond to clicks on QItems to
        change Toggle state.
      -->

      <q-item tag="label" v-ripple>
        <q-item-section avatar>
          <q-checkbox v-model="color" val="teal" color="teal" />
        </q-item-section>
        <q-item-section>
          <q-item-label>Teal</q-item-label>
        </q-item-section>
      </q-item>
    </q-list>
  </q-page>
</template>

<script>
export default {
}
</script>
