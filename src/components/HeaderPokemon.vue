<template>
  <div class="encabezado">
    <img
      src="https://upload.wikimedia.org/wikipedia/commons/thumb/9/98/International_Pok%C3%A9mon_logo.svg/1024px-International_Pok%C3%A9mon_logo.svg.png"
      alt="logo pokemon"
      class="logo-pokemon"
    />
    <h2 class="text-style">¿Quién es ese Pokémon?</h2>
    <div class="container-score">
      <p> Pokemones descubiertos: </p>
      <div class="container-points">
        <p class="score">SCORE</p>
        <span>{{ aciertos }}</span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "HeaderPokemon",
  props: ["aciertos"],
};
</script>

<style scoped>
@import url(https://fonts.googleapis.com/css?family=Bangers);
@import url('https://fonts.googleapis.com/css2?family=Tiny5&display=swap');

.encabezado {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.logo-pokemon {
  text-align: center;
  width: 40%;
  margin-bottom: 20px;
}

h2 {
  font-family: "Bangers";
  margin-bottom: 10px;
}

.text-style {
  font-size: 6vw;
  text-align: center;
  color: #fde026;
  text-shadow: 0 1px 0 #ddd, 0 2px 0 #ccc, 0 3px 0 #bbb, 0 4px 0 #aaa,
    0 5px 0 #acacac, 0 6px 1px rgba(0, 0, 0, 0.1), 0 0 5px rgba(0, 0, 0, 0.1),
    0 1px 3px rgba(0, 0, 0, 0.3), 0 3px 5px rgba(0, 0, 0, 0.2),
    0 5px 10px rgba(0, 0, 0, 0.25), 0 10px 10px rgba(0, 0, 0, 0.2),
    0 20px 20px rgba(0, 0, 0, 0.15);
    -webkit-text-stroke-width: 1px;
    -webkit-text-stroke-color: rgb(34, 42, 131);
}

p {
  padding: 10px 10px 0 10px;
  font-size: 2rem;
  font-family: "Tiny5", sans-serif;
  font-weight: 400;
  font-style: normal;
  text-align: center;
}

.container-score{
  margin: 0 auto;
  display: flex;
  align-items: center;
  justify-content: center;
  width: 60%;
}

.score{
  margin-bottom: 0;
  margin-top: 0;
  color: red;
}

.container-points{
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  background-color: white;
  border-radius: 10px;
  border: 5px solid blue;
}

span {
  color: orange;
  font-size: 4rem;
  font-family: "Tiny5", sans-serif;
  font-weight: 400;
  font-style: normal;
  margin-left: 7px;
}

@media screen and (max-width: 576px) {
  .logo-pokemon{
    width: 70%;
  }
  .container-score{
    flex-direction: column;
    align-items: center;
  }
}
</style>
