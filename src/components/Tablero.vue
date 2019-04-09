<template>
  <div class="tablero">
    <div class="niveles">
      <span>Nivel:</span>
      <span class="nivel">1</span>
      <span class="nivel">2</span>
      <span class="nivel">3</span>
    </div>
    <div class="panel">
      <div class="marcador minas-restantes">999</div>
      <div class="cara">
        <span>😋</span>
      </div>
      <div class="marcador segundos">
        999
      </div>
    </div>
    <div class="matriz">
      <cuadro v-for="(item, index) in cuadros" :key="index" :style="'grid-row: ' + item.fila + '; grid-column:' + item.columna + ';'"/>
    </div>
  </div>
</template>

<script>
import Cuadro from './Cuadro.vue'

export default {
  components: { Cuadro },
  data () {
    return {
      cuadros: [],
      nivelPrincipiante: {
        nivel: 1,
        filas: 9,
        columnas: 9,
        minas: 10
      },
      nivelIntermedio: {
        nivel: 2,
        filas: 16,
        columnas: 16,
        minas: 40
      },
      nivelExperto: {
        nivel: 3,
        filas: 16,
        columnas: 30,
        minas: 99
      },
      nivelActual: null
    }
  },
  created () {
    this.nivelActual = this.nivelPrincipiante
    this.iniciarNivel()
  },
  methods: {
    iniciarNivel () {
      let filas = this.nivelActual.filas
      let columnas = this.nivelActual.columnas
      let totalCuadros = filas * columnas

      this.cuadros = []

      for (let i = 0; i < totalCuadros; i++) {
        let cuadro = {
          fila: Math.floor(i / columnas) + 1,
          columna: (i % columnas) + 1
        }

        // console.log(i, cuadro.fila, cuadro.columna)
        

        this.cuadros.push(cuadro)
        
      }
    }
  }
}
</script>

<style>
  .tablero {
    display: grid;
    justify-content: center;
    background-color: #bdbdbd;
    padding: .5em;
  }

  .niveles {
    display: grid;
    grid-auto-flow: column;
  }

  .nivel {
    --tamanio: 32px;
    width: var(--tamanio);
    height: var(--tamanio);
  }
  
  .panel {
    display: grid;
    grid-auto-flow: column;
    font-size: 2em;
    text-align: center;
  }

  .marcador {
    background-color: black;
    color: red;
    height: 40px;
  }

  .minas-restantes {

  }

  .cara {

  }

  .segundos {

  }

  .matriz {
    display: grid;
    background-color: #7b7b7b;
  }
</style>