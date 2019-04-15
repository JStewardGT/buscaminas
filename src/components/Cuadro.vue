<template>
  <div
    @mousedown.right="bandera"
    @mouseup.left="activar"
    @contextmenu.prevent
    class="cuadro"
    :class="info.inicial ? 'cuadro-inicial': 'cuadro-vacio'"
  >
    <span :class="clase">{{ valor }}</span>
  </div>
</template>

<script>
export default {
  props: ["info"],
  computed: {
    valor() {
      if (this.info.inicial) {
        if (this.info.bandera) {
          return "🚩";
        } else {
          return "";
        }
      } else {
        return this.info.valor;
      }
    },
    clase() {
      if (this.info.inicial) {
        if (this.info.bandera) {
          return "bandera";
        } else {
          return "";
        }
      } else if (this.info.valor == "❌") {
        return "bandera-falsa";
      } else {
        return this.info.claseValor;
      }
    }
  },
  methods: {
    bandera() {
      if (this.info.inicial) {
        this.$emit("onCambiarMinasRestantes", this.info);
      }
    },
    activar() {
      this.$emit("onActivar", this.info);
    }
  }
};
</script>
<style>
.bandera {
  font-size: 12px;
}

.bandera-falsa {
  font-size: 18px;
}

.cuadro {
  display: grid;
  justify-content: center;
  align-items: center;
}

.cuadro-inicial {
  width: 20px;
  height: 20px;
  background-color: #bdbdbd;
  border-color: #fff #818181 #818181 #fff;
  border-style: solid;
  border-width: 3px;
  cursor: pointer;
}

.cuadro-vacio {
  width: 25px;
  height: 25px;
  border: solid 1px #7b7b7b;
  background: #bdbdbdbd;
  cursor: default;
}
</style>
