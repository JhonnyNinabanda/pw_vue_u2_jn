<template>
  <div>
    <label for="id_nombre">Nombre</label>
    <input v-model="nombre" id="id_nombre" type="text" />

    <label for="id_apellido">Apellido</label>
    <input v-model="apellido" id="id_apellido" type="text" />

    <p>Hola, {{ nombre }} {{ apellido }}</p>

    <h1>{{ arreglo }}</h1>

    <ul>
      <li v-show="nombre !== null" v-for="{ nombre, apellido } in arreglo" :key="nombre">
        {{ nombre }} {{ apellido }}
      </li>
    </ul>

    <h2>Tabla de Registros</h2>
    <div id="table-container">
      <table id="table">
        <thead>
          <tr>
            <th>Nombre</th>
            <th>Apellido</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="{ nombre, apellido } in arreglo" :key="nombre">
            <td v-show="nombre !== null">{{ nombre }}</td>
            <td v-show="apellido !== null">{{ apellido }}</td>
          </tr>
        </tbody>
      </table>
    </div>

    <button v-on:click="imprimirNombreApellido">Imprimir Nombre</button>
    <button v-on:click="agregarEstudiante">Imprimir Estudiante</button>
    <button v-on:click="limpiarFormulario">Limpiar Formulario</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      nombre: null,
      apellido: null,
      arreglo: [],
    };
  },
  methods: {
    imprimirNombreApellido() {
      console.log(this.nombre), console.log(this.apellido);
    },
    agregarEstudiante() {
      const stu = {
        nombre: this.nombre,
        apellido: this.apellido,
      };
      console.log("Agregar estudiante");
      console.log(stu);
      this.arreglo.push(stu);
    },
    limpiarFormulario() {
      this.nombre = null;
      this.apellido = null;
    },
  },
};
</script>

<style scoped>
/* ===== CONTENEDOR GENERAL ===== */
div {
  max-width: 500px;
  margin: 30px auto;
  padding: 25px;
  background: #ffffff;
  border-radius: 12px;
  box-shadow: 0 5px 20px rgba(0, 0, 0, 0.12);
  font-family: Arial, sans-serif;
}

/* ===== LABELS ===== */
label {
  display: block;
  margin-top: 15px;
  font-weight: bold;
  color: #444;
}

/* ===== INPUTS ===== */
input {
  width: 100%;
  padding: 10px;
  margin-top: 6px;
  border: 1px solid #ccc;
  border-radius: 6px;
  font-size: 15px;
  transition: 0.3s;
}

input:focus {
  border-color: #4a90e2;
  box-shadow: 0 0 5px rgba(74, 144, 226, 0.4);
  outline: none;
}

/* ===== LISTA ===== */
ul {
  margin-top: 20px;
  padding-left: 0;
}

ul li {
  list-style: none;
  background: #e8f1ff;
  padding: 10px;
  margin: 6px 0;
  border-radius: 6px;
  font-size: 16px;
  border-left: 4px solid #4a90e2;
}

/* ===== TABLA ===== */
#table-container {
  margin-top: 20px;
}

#table {
  width: 100%;
  border-collapse: collapse;
  margin-top: 10px;
  font-size: 16px;
}

#table th {
  background: #4a90e2;
  color: white;
  padding: 12px;
}

#table td {
  padding: 10px;
  border-bottom: 1px solid #ddd;
}

#table tr:nth-child(even) {
  background: #f5faff;
}

/* ===== BOTONES ===== */
button {
  margin-top: 15px;
  margin-right: 10px;
  padding: 10px 16px;
  background: #4a90e2;
  color: white;
  border: none;
  border-radius: 6px;
  cursor: pointer;
  font-size: 15px;
  transition: 0.3s;
}

button:hover {
  background: #357ac9;
}

button:active {
  transform: scale(0.97);
}
</style>
