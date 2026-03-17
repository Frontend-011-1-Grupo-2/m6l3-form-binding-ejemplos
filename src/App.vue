<template>
  <main class="container">
    <h1>Form binding con <code>v-model</code></h1>
    <FormEjemplo />
    <hr class="my-5">
    <FormValidado>
      <h2>Form Validado</h2>
    </FormValidado>
  </main>
</template>

<script>
// Como ocupar componentes externos?
/* 
1. import
2. registrar en el objeto components
3. usarlo en el template
*/
import FormEjemplo from './components/FormEjemplo.vue';
import FormValidado from './components/FormValidado.vue';
export default {
  name: 'App',
  // props: {},
  data: function () {
    return {}
  },
  // computed: {},
  //methods: {},
  // watch: {},
  components: {
    FormEjemplo,
    FormValidado
  },
  // mixins: [],
  // filters: {},
  // -- Lifecycle Methods
  // -- End Lifecycle Methods
}
</script>

<style scoped></style>