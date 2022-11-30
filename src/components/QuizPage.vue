<script setup lang="ts">
import { ref } from 'vue';
import { questions, choice1, choice2, choice3, choice4 } from './quiz'

const counter = ref(0)
const selection = ref(0)
const role = ref("")

const click = () => {
    if(choice1.value > choice2.value && choice1.value > choice3.value && choice1.value > choice4.value){
        role.value = "Left Brain"
    } else if(choice2.value > choice1.value && choice2.value > choice3.value && choice2.value > choice4.value){
        role.value = "Right Brain"
    } else if(choice3.value > choice1.value && choice3.value > choice2.value && choice3.value > choice4.value){
        role.value = "Artisan"
    } else if(choice4.value > choice1.value && choice4.value > choice2.value && choice4.value > choice3.value){
        role.value = "Brawn"
    } else {
        role.value = "Unknown"
    }

    switch(selection.value){
        case 1:
            choice1.value++
            break
        case 2:
            choice2.value++
            break
        case 3:
            choice3.value++
            break
        case 4:
            choice4.value++
            break
    }

    selection.value = 0
    if(counter.value < 11){
        counter.value++
    }
}
</script>

<template>
    <transition mode="out-in">
    <div v-if="counter < 11">
    <div class="pt-7">
    <transition mode="out-in">
    <div :key="counter" class="quesiton-container pt-8 d-flex flex-column align-center justify-space-between">
        <div class="d-flex flex-column align-center" :key="counter">
        <div class="question" :key="counter">
             {{ questions[counter][0] }}
        </div>
        <div class="pa-2" v-for="(item, idx) in questions[counter]" :key="idx">
            <div :key="counter" class="d-flex justify-center align-center choices" :class="selection === idx ? 'green' : '' " @click="selection=idx" v-if="idx != 0" v-ripple>
                <div class="pa-2">
                    {{ item }}
                </div>
            </div>
        </div>
        </div>
        <div class="pt-16">
        <div v-if="selection != 0" @click="click()" class="d-flex submit-button elevation-2 align-center justify-center" v-ripple>
            <div>
                SUBMIT
            </div>
        </div>
    <div v-else class="d-flex submit-button2 align-center justify-center">
        <div>
            SUBMIT
        </div>
    </div>
</div>
</div>
</transition>
</div>
</div>
<div v-else>
    <div class="d-flex flex-column justify-center align-center" v-if="role==='Unknown'">
        <div class="faction-text">
            Your faction is:
        </div>
        <div class="faction-text">
            <span style="color: #52b788">{{role}}</span>
        </div>
        <div class="description">
            Further testing is required
        </div>
    </div>
    <div class="d-flex flex-column align-center justify-center" v-else>
        <div class="faction-text">
            Your faction is:
        </div>
        <div class="faction-text">
            <span style="color: #52b788">{{role}}</span>
        </div>
    </div>
</div>
</transition>
</template>

<style scoped>
.v-enter-active,
.v-leave-active {
  transition: opacity 0.3s ease;
}

.v-enter-from,
.v-leave-to {
  opacity: 0;
}

.faction-text{
    font-size: 40px;
    user-select: none;
}
.green{
    background-color: #52b788;
    color: #edf2f4;
    box-shadow: rgba(50, 50, 93, 0.25) 0px 30px 60px -12px inset, rgba(0, 0, 0, 0.3) 0px 18px 36px -18px inset !important;
}

.submit-button2{
  user-select: none;
  width: 100px;
  height: 30px;
  background-color: grey;
  border-radius: 4px;
  font-weight: 700;
  text-align: center;
  font-size: 16px;
  color: #edf2f4;
  transition: all 0.5s ease;
  box-shadow: rgba(50, 50, 93, 0.25) 0px 50px 100px -20px, rgba(0, 0, 0, 0.3) 0px 30px 60px -30px, rgba(10, 37, 64, 0.35) 0px -2px 6px 0px inset;
}

.submit-button{
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
  transition: all 0.5s ease;
}
.question-container{
    height: 90vh;
}
.question{
    color: #52b788;
    font-size: 26px;
    text-align: center;
    font-weight: 500;
    user-select: none;
    height: 70px;
}

.choices{
    height: 50px;
    width: 500px;
    border-radius: 4px;
    text-align: center;
    cursor: pointer;
    font-size: 14px;
    user-select: none;
    box-shadow: rgba(0, 0, 0, 0.16) 0px 3px 6px, rgba(0, 0, 0, 0.23) 0px 3px 6px;
    transition: all 0.3s ease;
}

@media only screen and (max-width: 800px) {
    .choices{
        font-size: 14px;
        width: 300px;
    }

    .question{
        font-size: 18px;
    }

    .faction-text{
        font-size: 28px;
    }
}
</style>