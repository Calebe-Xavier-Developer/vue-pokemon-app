<template>
  <div class="p-14">
    <router-link class="flex justify-center text-4xl text-yellow-400 font-semibold leading-[24.5px] text-nowrap" to="/">Pokemon Picker</router-link>
  </div>
  <router-view/>
</template>

<style>
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    width: 100Vw;
    height: 100vh;
    background-color: #ff7d7d;
  }

  .custom-scrollbar::-webkit-scrollbar {
    width: 8px;
    height: 8px;
  }

  .custom-scrollbar::-webkit-scrollbar-track {
    background: none;
  }

  .custom-scrollbar::-webkit-scrollbar-thumb {
    background-color: #ffd900;
    border-radius: 28px;
  }

  .custom-scrollbar::-webkit-scrollbar-thumb:hover {
    background-color: none;
  }
  .custom-scrollbar::-webkit-scrollbar-corner {
    background: transparent;
  } 
</style>
