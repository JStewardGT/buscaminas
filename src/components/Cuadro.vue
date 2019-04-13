<template>
  <div class="cuadro cuadro-inicial">
    <span>{{ info.valor }}</span>
  </div>
</template>

<script>
export default {
  props: ['info']
}
</script>
<style>

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

</style>
