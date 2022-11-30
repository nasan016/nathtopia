<script setup lang="ts">
</script>

<template>
  <div class="main d-flex justify-center align-center flex-column">
    <div class="router-view pa-4 d-flex flex-column justify-space-between">
        <router-view/>
    </div>
  </div>
</template>

<style scoped>
.slide-fade-enter-active {
  transition: all 0.8s ease-out;
}
.slide-fade-leave-active {
  transition: all 0.3s ease-out;
}
.slide-fade-enter-from,
.slide-fade-leave-to {
  transform: translateX(20px);
  -webkit-transform: translateX(20px);
  -webkit-opacity: 0;
  opacity: 0;
}

.main{
  height: 100vh;
  width: 100vw;
  padding: 40px;
  overflow-x: hidden;
  overflow-y: hidden;
}

.router-view{
  width: 100%;
  height: 100%;
  border-radius: 8px;
  box-shadow: rgba(0, 0, 0, 0.24) 0px 3px 8px;
}

@media only screen and (max-width: 800px) {
  .router-view{
    width: 100%;
    height: 100%;
    border: none;
    justify-content: center;
    align-items: center;
    box-shadow: none;
  }

  .main{
    height: 90vh;
    width: 100vw;
    padding: 40px;
    overflow-x: hidden;
    overflow-y: hidden;
  }
}
</style>