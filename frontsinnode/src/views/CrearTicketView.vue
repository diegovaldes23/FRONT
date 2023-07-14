<template>
  <div class="CrearTicket">
    <h1 class="title">Creación de Ticket</h1>

    <div class="form-group">
      <label for="email">Coloca tu correo:</label>
      <input id="email" type="text" v-model="email" placeholder="Escribe tu correo aquí" />
    </div>

    <div class="form-group">
      <label for="rut">Coloque su RUT:</label>
      <input id="rut" type="text" v-model="rut" placeholder="Escribe tu RUT aquí" />
      <p v-if="isRutValid" class="valid-rut">RUT válido para Chile</p>
      <p v-else class="invalid-rut">RUT inválido</p>
    </div>

    <div class="form-group">
      <label for="subject">Asunto:</label>
      <textarea id="subject" v-model="subject" placeholder="Escribe el asunto aquí"></textarea>
    </div>

    <div class="form-group">
      <label for="area">Asignar Área:</label>
      <select id="area" v-model="area">
        <option value="">Selecciona un área</option>
        <option value="educacion">Educación</option>
        <option value="salud">Salud</option>
        <!-- Agrega más opciones según tus necesidades -->
      </select>
    </div>

    <!-- Agrega aquí cualquier otro contenido adicional que desees mostrar en la página -->

  </div>
</template>

<script setup>
import { ref, computed } from 'vue'

const email = ref('')
const rut = ref('')
const subject = ref('')
const area = ref('')

const isRutValid = computed(() => {
  // Lógica para validar el RUT aquí (puedes usar una librería de validación o implementar tu propia lógica)
  // Devuelve true si el RUT es válido, o false en caso contrario
  return isValidRut(rut.value)
})

// Función para validar el RUT
function isValidRut(rut) {
  // Implementa tu lógica de validación del RUT aquí
  // Retorna true si el RUT es válido, o false en caso contrario
}

</script>

<style>
/* Estilos adicionales para la página AboutView, si es necesario */
.about {
  max-width: 800px;
  margin: 0 auto;
  padding: 2rem;
}

.title {
  font-size: 2rem;
  margin-bottom: 1.5rem;
}

.form-group {
  margin-bottom: 2rem;
}

label {
  display: block;
  font-weight: bold;
  margin-bottom: 0.5rem;
}

input[type="text"],
textarea {
  width: 100%;
  padding: 0.5rem;
  font-size: 1rem;
  border: 1px solid #ccc;
  border-radius: 4px;
}

.valid-rut {
  color: green;
  margin-top: 0.5rem;
}

.invalid-rut {
  color: red;
  margin-top: 0.5rem;
}

select {
  width: 100%;
  padding: 0.5rem;
  font-size: 1rem;
  border: 1px solid #ccc;
  border-radius: 4px;
}

</style>