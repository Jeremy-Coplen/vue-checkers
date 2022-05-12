<script>
  import checkers from "../components/Checkers/Checkers.js"
  import spaces from "../components/Spaces/Spaces.js"

  export default {
    data() {
      return {
        checkers: checkers,
        spaces: spaces
      }
    },
    methods: {
      moveChecker(location, color, king) {},
      renderChecker(location) {
        let checker = this.checkers.find(checker => checker.location === location)
        if(checker) {
          return location === checker.location && checker.status === "alive"
        }
        else {
          return false
        }
      }
    }
  }
</script>

<template>
  <div class="game">
    <div id="red-dead-zone" class="dead-zone"></div>
    <div class="board">
      <div v-for="space in spaces" :key="space.id" :id="space.id" :class="['space', space.className]">
        <div v-if="renderChecker(space.location)" 
        :id="checkers.find(checker => checker.location === space.location).id" 
        :class="['checker', `checker-${checkers.find(checker => checker.location === space.location).color}`]" 
        @click="moveChecker(checkers.find(checker => checker.location === space.location).location, 
        checkers.find(checker => checker.location === space.location).color, 
        checkers.find(checker => checker.location === space.location).king)"></div>
      </div>
    </div>
    <div id="black-dead-zone" class="dead-zone"></div>
  </div>
</template>

<style>
  .game {
    display: flex;
    flex-direction: row;
    justify-content: space-around;
    align-items: center;
    width: 98vw;
    height: 79vh;
  }

  .dead-zone {
    display: flex;
    flex-direction: row;
    justify-content: flex-start;
    align-items: center;
    width: 18vw;
    height: 56vh;
  }

  #red-dead-zone {
    background-color: black
  }

  #black-dead-zone {
    background-color: #DBC3A1;
  }

  .board {
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
    align-items: flex-start;
    flex-wrap: wrap;
    width: 56vw;
    height: 56vh;
  }

  .space {
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
    width: 7vw;
    height: 7vh;
  }

  .space-tan {
    background-color: #DBC3A1;
  }

  .space-black {
    background-color: black;
  }

  .checker {
    width: 3vw;
    height: 3vw;
    border-radius: 50%;
  }

  .checker-red {
    background-color: red;
  }

  .checker-black {
    background-color: black;
    border: 1px solid white;
  }
</style>