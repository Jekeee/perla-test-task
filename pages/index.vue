<template>
  <main class="main">
    <Header :basketList="basketList" />
    <Product-info :basketList="basketList" />
  </main>
</template>

<script >
export default {
  data: () => {
    return {
      basketList: [
      ]
    }
  }
}
</script>

<style>
*,
*::before,
*::after {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

a {
  color: inherit;
  text-decoration: none;
  transition: .3s;
}

img {
  max-width: 100%;
}

ul li {
  list-style: none;
}

button {
  display: block;
  border: none;
  font: inherit;
  background-color: transparent;
  cursor: pointer;
  transition: .3s;
}

.container {
  max-width: 1306px;
  margin: 0 auto;
  padding: 0 5px;
}

.main {
  background: url(../static/background.jpg);
  background-repeat: no-repeat;
  background-size: cover;
  font-family: 'Onest', Arial, Helvetica, sans-serif;
  color: #1D1D1B;
}


@media (max-width: 1320px) {
  .container {
    max-width: 768px;
    margin: 0 auto;
    padding: 0 5px;
  }
}

@media (max-width: 768px) {
  .container {
    max-width: 384px;
    margin: 0 auto;
    padding: 0 5px;
  }
}
</style>
