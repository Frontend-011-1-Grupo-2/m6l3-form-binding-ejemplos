<script>
export default {
  name: 'FormEjemplo',
  data() {
    return {
      nombre: 'Juanin',
      edad: null,
      comentario: 'Comentario desde el modelo de datos',
      aceptaTyc: false,
      intereses: [],
      pastoEsVerde: '',
      platoPreferido: '',
      personajes: []
    }
  },
  methods: {
    handleInput($event) {
      this.nombre = $event.target.value
    }
  }
}
</script>

<template>
  <form>
    <!-- v-bind es enlazado unidireccional: desde datos hacia la vista y no vice versa -->
    <!-- <input type="text" name="nombre" id="nombre" v-bind:value="nombre" @input="handleInput"> -->

    <!-- limpia inicio y fin de la cadena (quita espacios en blanco) -->
    <input class="form-control" type="text" name="nombre" id="nombre" v-model.trim="nombre">
    <div>
      <label for="edad">Edad</label>
      <!-- .number convierte el input (string) en un número -->
      <!-- si es que la transformación a número no es posible, se entrega el string original -->
      <input class="form-control" type="text" v-model.number="edad">
    </div>
    <div>
      <!-- modificador .lazy espera a que se pierda el foco del input para actualizar el dato -->
      <!-- sin el .lazy se hace caracter por caracter -->
      <textarea class="form-control" name="comentario" id="comentario" v-model.lazy="comentario"></textarea>
    </div>
    <div>
      <!-- checkbox almacena un valor booleano (si/no, true/false, encendido/apagado) -->
      <div class="form-check">
        <input class="form-check-input" type="checkbox" name="tyc" id="tyc" v-model="aceptaTyc">
        <label class="form-check-label" for="tyc">Acepto los términos y condiciones</label>

      </div>
    </div>
    <div>
      <h3>Intereses</h3>
      <p>Selecciona tus intereses:</p>
      <!-- todos los siguientes checkboxes apuntan a la misma variable (array 'intereses') -->
      <!-- cuando se marca uno, automaticamente hace un push de su value ('ia', 'cloud', 'frontend') -->
      <div class="form-check">

        <input class="form-check-input" type="checkbox" id="ia" name="ia" value="ia" v-model="intereses">
        <label class="form-check-label" for="ia">IA</label>
      </div>

      <div class="form-check">
        <input class="form-check-input" type="checkbox" id="cloud" name="cloud" value="cloud" v-model="intereses">
        <label class="form-check-label" for="cloud">Cloud</label>
      </div>

      <div class="form-check">
        <input class="form-check-input" type="checkbox" id="frontend" name="frontend" value="frontend"
          v-model="intereses">
        <label class="form-check-label" for="frontend">Frontend</label>
      </div>
    </div>
    <div>
      <h3>Responda la pregunta</h3>
      <h5>¿El pasto es verde?</h5>
      <div class="form-check">
        <input class="form-check-input" type="radio" value="falso" v-model="pastoEsVerde">Falso</input>
      </div>
      <div class="form-check">
        <input class="form-check-input" type="radio" value="verdadero" v-model="pastoEsVerde">Verdadero</input>
      </div>
      <div class="form-check">
        <input class="form-check-input" type="radio" value="ninguna" v-model="pastoEsVerde">Ninguna de las
        anteriores</input>
      </div>
    </div>

    <div>
      <h3>Elige un plato <small>select de selección única</small></h3>
      <select class="form-select" name="platos" id="platos" v-model="platoPreferido">
        <option value="charquican">Charquicán</option>
        <option value="porotos">Porotos con riendas</option>
        <option value="asado">Asado</option>
      </select>
    </div>

    <div>
      <h3>Selecciona tus personajes favoritos</h3>
      <select class="form-select" name="personajes" id="personajes" multiple="true" v-model="personajes">
        <option value="Goku">Goku</option>
        <option value="Neo">Neo</option>
        <option value="Ash">Ash</option>
        <option value="Donatello">Donatello</option>
      </select>
    </div>
    <section>
      <h2>Nombre almacenado en <code>data()</code>: {{ nombre }}</h2>
    </section>
  </form>
</template>

<style scoped>
code {
  color: lightcoral
}
</style>
