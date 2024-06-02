<template>
  <div id="app">
    <main class="container">
      <h1 class="text-center fw-bold py-3">Modifica tu texto</h1>
      <hr />
      <div class="row">
        <div class="col-12 col-md-6 divForm">
          <form>
            <ul>
              <div class="py-2">
                <li>
                  <label for="colorFondo">Color de fondo: </label>
                  <input
                    type="color"
                    id="colorFondo"
                    value="#0400ff"
                    v-model="colFondo"
                  />
                </li>
              </div>
              <div class="py-2">
                <li>
                  <label for="colorTexto">Color de texto: </label>
                  <input
                    type="color"
                    id="colorTexto"
                    value="#ffffff"
                    v-model="colTexto"
                  />
                </li>
              </div>
              <div class="py-2">
                <li>
                  <label for="mostrarTexto">¿Mostrar texto?: </label>
                  <input
                    type="checkbox"
                    id="mostrarTexto"
                    value="0"
                    v-model="mosTexto"
                  />
                </li>
              </div>
              <div class="py-2">
                <li>
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
                </li>
              </div>
              <div class="py-2">
                <li>
                  <label for="contenidoTexto">Contenido texto: </label>
                  <textarea
                    name="contenidoTexto"
                    id="contenidoTexto"
                    v-model="conTexto"
                  ></textarea>
                </li>
              </div>
              <div class="py-2">
                <li>
                  <label for="tipoLetra">Estilo de letra:</label>
                  <select name="tipoLetra" id="tipoLetra" v-model="estTexto">
                    <option value="normal" selected>Normal</option>
                    <option value="italic">Cursiva</option>
                  </select>
                </li>
              </div>
              <div class="py-2">
                <li>
                  <label for="textoOpaco">Opacidad: </label>
                  <input
                    type="range"
                    name="textoOpaco"
                    id="textoOpaco"
                    min="0"
                    max="1"
                    step="0.01"
                    v-model="opaTexto"
                  />
                </li>
              </div>
              <div class="py-2">
                <li>
                  <label for="tipografia">Tipografía:</label>
                  <select name="tipografia" id="tipografia" v-model="fontTexto">
                    <option value="" selected disabled>Seleccione...</option>
                    <option
                      v-for="tipografia in tipografias"
                      :key="tipografia.id"
                      :value="tipografia.font"
                    >
                      {{ tipografia.font }}
                    </option>
                  </select>
                </li>
              </div>
              <div class="py-2">
                <li>
                  <label>Tamaño de texto:</label>
                  <input
                    class="mx-2"
                    type="radio"
                    value="textoPequeno"
                    v-model="tamTexto"
                  />
                  Pequeño
                  <input
                    class="mx-2"
                    type="radio"
                    value="textoMediano"
                    v-model="tamTexto"
                  />
                  Mediano
                  <input
                    class="mx-2"
                    type="radio"
                    value="textoGrande"
                    v-model="tamTexto"
                  />
                  Grande
                </li>
              </div>
            </ul>
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
              :class="{
                textoPequeno: tamTexto == 'textoPequeno',
                textoMediano: tamTexto == 'textoMediano',
                textoGrande: tamTexto == 'textoGrande',
              }"
              :style="{
                color: colTexto,
                fontStyle: estTexto,
                fontFamily: fontTexto,
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
      tamTexto: "",
      tipografias: [
        { id: 1, name: "Arial", font: "Arial" },
        { id: 2, name: "Lucida Console", font: "Lucida" },
      ],
      fontTexto: "",
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
  font-family: monospace;
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
.textoPequeno {
  font-size: 15px;
}

.textoMediano {
  font-size: 25px;
}

.textoGrande {
  font-size: 35px;
}
</style>
