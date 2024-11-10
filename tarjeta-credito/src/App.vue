<script>
  export default {
    name:"App",
    data() {
      return {
        cardTitle: '',            // Título de la tarjeta
        chipSrc: '',              // Ruta por defecto del chip
        cardNumber: '',           // Número de tarjeta por defecto
        expirationDate: '',       // Fecha de expiración por defecto
        ownerName: '',            // Nombre del propietario por defecto
        cardTypeSrc: ''           // Tipo de tarjeta (Visa) por defecto
      };
    },
    computed: {
      // Formatear el número de tarjeta para hacerlo más legible
      formattedCardNumber() {
        return this.cardNumber.replace(/(\d{4})(?=\d)/g, '$1 ');
      }
    }
  };
</script>

<template>
  <div id="app">
    <!-- Formulario de tarjeta -->
    <form>
      <div>
        <label>Título de la tarjeta: </label>
        <input v-model="cardTitle" />
      </div>

      <div>
        <label>Chip SRC: </label>
        <input v-model="chipSrc" />
      </div>

      <div>
        <label>Número: </label>
        <input v-model="cardNumber" />
      </div>

      <div>
        <label>Fecha de expiración: </label>
        <input v-model="expirationDate" />
      </div>

      <div>
        <label>Propietario: </label>
        <input v-model="ownerName" />
      </div>

      <div>
        <label>Tipo de tarjeta SRC: </label>
        <input v-model="cardTypeSrc" />
      </div>
    </form>

    <!-- Visualización de la tarjeta -->
    <div class="carnet">
      <h3>{{ cardTitle }}</h3>
      <img :src="chipSrc" width="40" alt="Chip" />
      <div class="fechaExp">
        <h2>{{ formattedCardNumber }}</h2>
        <span class="fecha">Fecha Exp: <b>{{ expirationDate }}</b></span>
      </div>
      <footer>
        <span>{{ ownerName }}</span>
        <img :src="cardTypeSrc" width="60" alt="Visa" />
      </footer>
    </div>
  </div>
</template>

<style scoped>
  * {
    margin: 0;
  }
  body {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 60vh;
    font-size: 10px;
    font-family: sans-serif;
  }

  #app {
    display: flex;
    gap: 40px;
  }
  form {
    padding: 18px;
    border-radius: 20px;
    border: ridge 1px;
    box-shadow: 1px 1px 1px 1px gray;
    font-weight: bold;
    display: flex;
    flex-direction: column;
    gap: 15px;
    justify-content: center;
  }
  form div {
    display: grid;
    grid-template-columns: 100px 200px;
    align-items: center;
    gap: 5px;
  }

  form div label {
    text-align: right;
  }

  .carnet {
    width: 400px;
    height: 230px;
    background: #1c1a1e;
    color: white;
    border-radius: 20px;
    padding: 20px;
    box-shadow: 0px 0px 10px 2px black;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
  }

  h3 {
    font-size: 20px;
    text-align: start;
  }

  h2 {
    font-size: 30px;
    letter-spacing: 10px;
    margin-bottom: 15px;
    text-shadow: 0px 0px 1px gold;
    font-family: Times;
  }

  .fecha{
    font-size: 10px;
  }

  .fechaExp{
    text-align: start;
  }

  b {
    font-size: 16px;
  }

  footer {
    display: flex;
    justify-content: space-between;
    align-items: flex-end;
    font-weight: bold;
    font-size: 18px;
    text-transform: uppercase;
    font-style: italic;
  }
</style>
