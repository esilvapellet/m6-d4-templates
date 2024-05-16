<template>
  <div id="app">
    <main class="container">
      <h1 class="text-center fw-bold py-3">Modifica tu texto</h1>
      <hr />
      <div class="row">
        <div class="col-12 col-md-6 divForm">
          <form>
            <div>
              <label for="colorFondo">Color de fondo: </label>
              <input
                type="color"
                id="colorFondo"
                value="#0400ff"
                v-model="colFondo"
              />
            </div>
            <div>
              <label for="colorTexto">Color de texto: </label>
              <input
                type="color"
                id="colorTexto"
                value="#ffffff"
                v-model="colTexto"
              />
            </div>
            <div>
              <label for="mostrarTexto">¿Mostrar texto?: </label>
              <input
                type="checkbox"
                id="mostrarTexto"
                value="0"
                v-model="mosTexto"
              />
            </div>
            <div>
              <label for="bordeTexto">Redondeado: </label>
              <input
                type="range"
                name="bordeTexto"
                id="bordeTexto"
                min="0"
                max="200"
                step="1"
                value="0"
                v-model="borTexto"
              />
            </div>
            <div>
              <label for="contenidoTexto">Contenido textual: </label>
              <textarea
                name="contenidoTexto"
                id="contenidoTexto"
                v-model="conTexto"
              ></textarea>
            </div>
            <div>
              <label for="tipoLetra">Estilo de letra:</label>
              <select name="tipoLetra" id="tipoLetra" v-model="estTexto">
                <option value="normal" selected>Normal</option>
                <option value="italic">Cursiva</option>
              </select>
            </div>
            <div>
              <label for="textoOpaco">Opaco: </label>
              <input
                type="range"
                name="textoOpaco"
                id="textoOpaco"
                min="0"
                max="1"
                step="0.01"
                v-model="opaTexto"
              />
            </div>
            <div>
              <p>Tamaño de texto:</p>
              <input
                type="radio"
                name="radio1"
                id="radio1"
                value="10px"
                v-model="tamTexto"
              />
              <label for="radio1"> Pequeño </label>
              <input
                type="radio"
                name="radio2"
                id="radio2"
                value="20px"
                v-model="tamTexto"
              />
              <label for="radio1"> Mediano </label>
              <input
                type="radio"
                name="radio3"
                id="radio3"
                value="30px"
                v-model="tamTexto"
              />
              <label for="radio1"> Grande </label>
            </div>
          </form>
        </div>
        <div class="col-12 col-md-6 divCaja">
          <div
            class="cajaTexto"
            :style="{
              backgroundColor: colFondo,
              borderRadius: borTexto + 'px',
              opacity: opaTexto,
            }"
          >
            <span
              class="textoUsuario"
              :style="{
                color: colTexto,
                fontSize: tamTexto,
                fontStyle: estTexto,
              }"
              v-show="mosTexto"
            >
              {{ conTexto }}
            </span>
          </div>
        </div>
      </div>
    </main>
  </div>
</template>

<script>
export default {
  name: "App",
  components: {},
  data() {
    return {
      colFondo: "#0400ff",
      colTexto: "#ffffff",
      mosTexto: true,
      borTexto: "0",
      conTexto: " ",
      estTexto: "normal",
      opaTexto: 1,
      tamTexto: "20px",
    };
  },
  methods: {
    colFondo2: function () {
      return `${this.colFondo + this.opaTexto} `;
    },
  },
};
</script>

<style>
* {
  box-sizing: boder-box;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /* text-align: center;
  color: #2c3e50;
  margin-top: 60px; */
}
.cajaTexto {
  height: 400px;
  width: 400px;
  display: flex;
  align-items: center;
  justify-content: center;
}

.divForm,
.divCaja {
  display: flex;
  align-items: center;
  justify-content: center;
}

#contenidoTexto,
.cajaTexto {
  text-transform: capitalize;
}

#textoCaja {
  display: block;
  width: 80%;
  z-index: 2;
}

#textoUsuario {
  opacity: 0;
  z-index: 1;
}
</style>
