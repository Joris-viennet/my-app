<template>
  <div class="content">
    <h1 class="fat">404</h1>
    <h2>UH OH! You're lost.</h2>
    <p>
      The page you are looking for does not exist. How you got here is a mystery. But you can click
      the button below to go back to the homepage.
    </p>
    <a href="#/">
      <button class="btn">HOME</button>
    </a>
  </div>
</template>

<style scoped>
.content {
  margin: 10%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  text-align: center;
  align-items: center;
}

.fat {
  font-size: 10em;
  margin: 0;
  color: #42b883;
}
</style>
