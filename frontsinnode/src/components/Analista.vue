<template>
  <div class="assignment-page">
    <h1 class="page-title">Asignación de Analista</h1>

    <div class="content-container">
      <div class="table-section">
        <h2 class="section-title">Tickets</h2>
        <table>
          <thead>
            <tr>
              <th>ID</th>
              <th>Descripción</th>
              <th>Estado</th>
              <th>Seleccionar</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="ticket in tickets" :key="ticket.id">
              <td>{{ ticket.id }}</td>
              <td>{{ ticket.descripcion }}</td>
              <td>{{ ticket.estado }}</td>
              <td>
                <button
                  class="select-button"
                  @click="selectTicket(ticket)"
                  :disabled="selectedTicket || assignedTicket"
                >
                  Seleccionar
                </button>
              </td>
            </tr>
          </tbody>
        </table>
      </div>

      <div class="table-section">
        <h2 class="section-title">Analistas</h2>
        <table>
          <thead>
            <tr>
              <th>ID</th>
              <th>Nombre</th>
              <th>Especialidad</th>
              <th>Seleccionar</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="analista in analistas" :key="analista.id">
              <td>{{ analista.id }}</td>
              <td>{{ analista.nombre }}</td>
              <td>{{ analista.especialidad }}</td>
              <td>
                <button
                  class="select-button"
                  @click="selectAnalista(analista)"
                  :disabled="selectedAnalista || assignedTicket"
                >
                  Seleccionar
                </button>
              </td>
            </tr>
          </tbody>
        </table>
      </div>

      <div class="selected-options">
        <p class="selected-ticket" v-if="selectedTicket">Ticket seleccionado: {{ selectedTicket.descripcion }}</p>
        <p class="selected-analista" v-if="selectedAnalista">Analista seleccionado: {{ selectedAnalista.nombre }}</p>
      </div>

      <button class="assign-button" :disabled="!selectedTicket || !selectedAnalista || assignedTicket" @click="assignAnalyst">
        Asignar
      </button>

      <p v-if="assignedTicket" class="notification">Se logró asignar correctamente un analista al ticket.</p>
    </div>
  </div>
</template>

<script>
import { ref } from 'vue'

export default {
  data() {
    return {
      tickets: [
        { id: 1, descripcion: 'Ticket 1', estado: 'Abierto' },
        { id: 2, descripcion: 'Ticket 2', estado: 'En progreso' },
        { id: 3, descripcion: 'Ticket 3', estado: 'Cerrado' },
      ],
      analistas: [
        { id: 1, nombre: 'Analista 1', especialidad: 'Especialidad 1' },
        { id: 2, nombre: 'Analista 2', especialidad: 'Especialidad 2' },
        { id: 3, nombre: 'Analista 3', especialidad: 'Especialidad 3' },
      ],
      selectedTicket: null,
      selectedAnalista: null,
      assignedTicket: false,
    }
  },
  methods: {
    selectTicket(ticket) {
      this.selectedTicket = ticket
    },
    selectAnalista(analista) {
      this.selectedAnalista = analista
    },
    assignAnalyst() {
      console.log(`Asignando el ticket "${this.selectedTicket.descripcion}" al analista "${this.selectedAnalista.nombre}"`)
      this.assignedTicket = true
    },
  },
}
</script>

<style scoped>
.assignment-page {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100vh;
}

.page-title {
  font-size: 2rem;
  font-weight: bold;
  margin-bottom: 2rem;
  color: var(--color-heading);
}

.content-container {
  width: 100%;
  max-width: 1280px;
  margin: 0 auto;
  padding: 2rem;
  background-color: var(--color-background-light);
  border-radius: 4px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.table-section {
  margin-bottom: 2rem;
}

.section-title {
  font-size: 1.5rem;
  font-weight: bold;
  margin-bottom: 1rem;
  color: var(--color-heading);
}

.assign-button {
  padding: 0.5rem 1rem;
  font-size: 1.2rem;
  font-weight: bold;
  color: var(--color-text);
  background-color: var(--color-background-light);
  border: 2px solid var(--color-border);
  border-radius: 4px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.assign-button:hover {
  background-color: var(--color-background-light-hover);
}

.select-button {
  padding: 0.5rem 1rem;
  font-size: 1rem;
  font-weight: bold;
  color: var(--color-text);
  background-color: var(--color-background-light);
  border: 2px solid var(--color-border);
  border-radius: 4px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.select-button:hover {
  background-color: var(--color-background-light-hover);
}

.selected-options {
  margin-top: 2rem;
}

.selected-ticket,
.selected-analista {
  font-size: 1rem;
  margin-bottom: 0.5rem;
}

.notification {
  font-size: 1rem;
  margin-top: 1rem;
  color: green;
}

table {
  width: 100%;
  border-collapse: collapse;
}

th,
td {
  padding: 0.5rem;
  border-bottom: 1px solid var(--color-border);
}

th {
  font-weight: bold;
  text-align: left;
}

tbody tr:nth-child(even) {
  background-color: var(--color-background-lighter);
}

button:disabled {
  opacity: 0.5;
  cursor: not-allowed;
}
</style>
