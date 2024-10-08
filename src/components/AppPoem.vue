<script setup lang="ts">
import { ref } from 'vue'
import AppCheckbox from './AppCheckbox.vue'
import TextBlock from './TextBlock.vue'

const selectText = ref([true, true, true, true])

function changeState(id: number) {
  let countFalseState = 0
  selectText.value.forEach((item) => {
    if (item === false) {
      countFalseState++
    }
  })
  if (countFalseState === 3 && selectText.value[id] === true) {
    return
  }
  selectText.value[id] = !selectText.value[id]
}
</script>

<template>
  <div class="poem-wrapper">
    <div class="poem-block">
      <div class="title-block">
        <h1 class="title">Invictus</h1>
        <p class="name-author">By William Ernest Henley</p>
      </div>
      <div class="poem-body">
        <div class="controls">
          <AppCheckbox
            v-for="(state, index) of selectText"
            @changeState="changeState"
            :id="index"
            :state="state"
            :key="index"
          />
        </div>
        <TextBlock v-if="selectText[0]">
          <p>Out of the night that covers me,</p>
          <p>Black as the pit from pole to pole,</p>
          <p>I thank whatever gods may be</p>
          <p>For my unconquerable soul.</p>
        </TextBlock>
        <TextBlock v-if="selectText[1]">
          <p>In the fell clutch of circumstance</p>
          <p>I have not winced nor cried aloud.</p>
          <p>Under the bludgeonings of chance</p>
          <p>My head is bloody, but unbowed.</p>
        </TextBlock>
        <TextBlock v-if="selectText[2]">
          <p>Beyond this place of wrath and tears</p>
          <p>Looms but the Horror of the shade,</p>
          <p>And yet the menace of the years</p>
          <p>Finds and shall find me unafraid.</p>
        </TextBlock>
        <TextBlock v-if="selectText[3]">
          <p>It matters not how strait the gate,</p>
          <p>How charged with punishments the scroll,</p>
          <p>I am the master of my fate,</p>
          <p>I am the captain of my soul.</p>
        </TextBlock>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.poem-wrapper {
  display: flex;
  justify-content: center;
  color: #000;
}

.controls {
  position: absolute;
  right: calc(100% + 5%);
  display: flex;
  gap: calc(0.5em + 0.5vw);
}

.poem-block {
  position: relative;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.title-block {
  margin-right: calc(1em + 4vw);
  position: relative;
  display: flex;
  align-items: flex-end;
  margin-bottom: 20px;
  gap: 70px;
}

.title {
  font-size: calc(1em + 2.5vw);
}

.name-author {
  position: absolute;
  left: calc(100% + 30%);
  white-space: nowrap;
  margin-bottom: 5px;
  font-size: calc(16px + (22 - 16) * ((100vw - 480px) / (1024 - 480)));
}

.poem-body {
  white-space: nowrap;
  min-height: 100px;
  width: 25vw;
  font-size: calc(16px + (22 - 16) * ((100vw - 480px) / (1024 - 480)));
}
</style>
