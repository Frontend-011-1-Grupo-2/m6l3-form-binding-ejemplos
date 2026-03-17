<template>
  <form @submit.prevent="onLogin">
    <slot>
      <!-- El padre inyectará html -->
    </slot>
    <div>
      <label for="email">Email</label>
      <input type="email" v-model="usuario.email">
      <small class="input-error" v-if="usuario.email.length && !esMailValido">Error: el email es inválido</small>
    </div>
    <div>
      <label for="password">Password</label>
      <input type="password" v-model="usuario.password">
      <small class="input-error" v-if="usuario.password.length && !esPasswordValida">Contraseña inválida</small>
    </div>
    <button type="submit">Login</button>
  </form>
</template>

<script>
// Valida formato email (mail@mail.com)
const regexMail = /[a-z0-9!#$%&'*+/=?^_`{|}~-]+(?:\.[a-z0-9!#$%&'*+/=?^_`{|}~-]+)*@(?:[a-z0-9](?:[a-z0-9-]*[a-z0-9])?\.)+[a-z0-9](?:[a-z0-9-]*[a-z0-9])?/

// Valida que en la contraseña no puedan haber numeros consecutivos
const regexPass = /\d{2,}/

export default {
  name: 'FormValidado',
  // props: {},
  data: function () {
    return {
      usuario: {
        email: '',
        password: ''
      }
    }
  },
  computed: {
    esMailValido() {
      return regexMail.test(this.usuario.email)
    },
    esPasswordValida() {
      // return this.usuario.password.length >= 6
      return this.usuario.password.length >= 6 && !regexPass.test(this.usuario.password)
    },
    esFormValido() {
      return this.esMailValido && this.esPasswordValida
    }
  },
  methods: {
    onLogin() {
      if (this.esFormValido) {
        console.log('Login realizado exitosamente')
        console.log(this.usuario)
      } else {
        console.warn('El formulario contiene errores')
      }
    }
  },
  // watch: {},
  // components: {},
  // mixins: [],
  // filters: {},
  // -- Lifecycle Methods
  // -- End Lifecycle Methods
}
</script>

<style scoped>
.input-error {
  color: lightcoral
}
</style>