<template>
  <form @submit.prevent="handleLogin">
    <h2>Iniciar Sesión</h2>

    <div>
      <label>Nombre de usuario:</label>
      <input v-model="username" type="text" required />
    </div>

    <div>
      <label>Contraseña:</label>
      <input v-model="password" type="password" required />
    </div>

    <div>
      <label>Tipo de usuario:</label>
      <select v-model="userType">
        <option value="Usuario">Usuario</option>
        <option value="Administrador">Administrador</option>
      </select>
    </div>

    <button type="submit">Ingresar</button>
  </form>
</template>

<script setup>
import { ref } from 'vue'

const username = ref('')
const password = ref('')
const userType = ref('Usuario')

const handleLogin = () => {
  console.log('Login:', { username: username.value, password: password.value, userType: userType.value })
}
</script>
