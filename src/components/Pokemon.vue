<template>
  <div class="container-detalles">
    <img :src="detallePokemon.imagen" alt="imagen pokemon" />
    <h1>Habilidades</h1>
    <section class="containerSkill">
      <div v-for="(habilidad, index) in detallePokemon.habilidades" :key="index">
        <p>{{ habilidad.ability.name }}</p>
      </div>
    </section>
    <h1>Movimientos</h1>
    <div class="caja">
       <section class="containerMovimientos">
      <div v-for="(movimientos, index) in detallePokemon.movimientos" :key="index">
        <p>{{ movimientos.move.name }}</p>
      </div>
    </section>
    </div>
   
  </div>
</template>
<script>
export default {
  name: "Pokemon",
  props: {
    detallePokemon: {},
  },
};
</script>
<style scoped>
.container-detalles {
  height: 100%;
  width: 100%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

img {
  height: auto;
  width: 20%;
}
.caja{
width: 50%;
border:2px black solid;
padding:10px;
margin-bottom:20px;
}


.containerSkill, .containerMovimientos {
 display:flex;
flex-direction: row;
flex-wrap: wrap;
justify-content:space-between;
padding:10px
}

p {
  margin: 2px;
  padding: 10px;
  border:2px black solid;
  color: rgb(0, 0, 0);
  font-weight: 600;
  background-color: rgba(0, 0, 0, 0.199);
}


</style>
