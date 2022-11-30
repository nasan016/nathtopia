<script setup lang="ts">
</script>

<template>
  <div class="mobile-only">
  <div class="pl-4 title">
    Nath<span style="color: #74c69d">topia.</span>
  </div>
  <div>
    <div class="pl-4 pb-2 description">
      sector placement test
    </div>
  </div>
  <div class="pl-4 booton">
    <div class="enter-button elevation-2 d-flex justify-center align-center" v-ripple>
        <router-link :to="'\quiz'">
        <div class="enter-text">
        ENTER ►
        </div>
    </router-link>
    </div>
</div>
  </div>
  <div class="d-flex secondary-title justify-end pr-2" id="we-are-you">
    <div class="pb-4">
      <div class="text-container">
        we
      </div>
      <div class="text-container">
        are
      </div>
      <div class="text-container">
        you
      </div>
    </div>
  </div>
</template>

<style>
@import '../assets/base.css';
.enter-button{
  cursor: pointer;
  user-select: none;
  width: 100px;
  height: 30px;
  background-color: #52b788;
  border-radius: 4px;
  font-weight: 700;
  text-align: center;
  font-size: 16px;
  color: #edf2f4;
  transition: all 0.2s ease;
}

.enter-button:hover{
    background-color: #95d5b2;
}

.enter-text{
    text-decoration: none;
    color: #edf2f4
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

.name{
  font-size: 34px;
  font-weight: 500;
  user-select: none;
}

.description{
  font-size: 18px;
  font-weight: 700px;
  user-select: none;
  color: #6c757d;
}

.title{
  font-family: ava;
  font-size: 90px;
  height: 100px;
  user-select: none;
}

.secondary-title{
  font-size: 50px;
  line-height: 40px;
  font-family: Atiba;
  user-select: none;
}

.text-container{
  width: 100px;
  text-align: right;
  color: #343a40;
}

@media only screen and (max-width: 800px) {

  .mobile-only{
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }

  .text-container{
    text-align: center;
  }

  .title{
    font-size: 70px;
  }

  .description{
    padding-right: 14px;
  }

  .booton{
    padding-right: 14px !important;
  }
}
</style>