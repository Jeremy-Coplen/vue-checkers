<script>
  import checkers from "../components/Checkers/Checkers.js"
  import spaces from "../components/Spaces/Spaces.js"

  export default {
    data() {
      return {
        checkers: checkers,
        spaces: spaces,
        location: 0,
        clicked: false,
        turn: "black"
      }
    },
    methods: {
      checkMoves(location, color, king) {
        if(this.clicked) {
          return
        }
        else {
          if(this.turn === "black") {
            if(color === "black") {
              if(king) {
    
              }
              else {
                if(document.getElementById(`space-${location + 7}`).childNodes[0].nodeName === "DIV") {
                    if(document.getElementById(`space-${location + 7}`).childNodes[0].className.includes("checker-red")) {
                      if(document.getElementById(`space-${location + 14}`).childNodes[0].nodeName === "DIV") {
                        console.log("hit")
                        if(document.getElementById(`space-${location - 9}`).childNodes[0].nodeName === "DIV") {
                          if(document.getElementById(`space-${location - 9}`).childNodes[0].className.includes("checker-red")) {
                            if(document.getElementById(`space-${location - 18}`).childNodes[0].nodeName === "DIV") {
                              alert("Unable to move checker")
                              return
                            }
                            else {
                              this.location = location
                              this.clicked = true
                            }
                          }
                          else {
                            alert("Unable to move checker")
                            return
                          }
                        }
                        else {
                          this.location = location
                          this.clicked = true
                          return
                        }
                      }
                      else {
                        this.location = location
                        this.clicked = true
                        return
                      }
                    }
                    else {
                      alert("Unable to move checker")
                      return
                    }
                  }
                else {
                  this.location = location
                  this.clicked = true
                  return
                }
              }
            }
            else {
              alert("It is black's turn")
              return
            }
          }
          else {
            if(color === "red") {
              if(king) {
    
              }
              else {
                if(document.getElementById(`space-${location + 9}`).childNodes[0].nodeName === "DIV") {
                    if(document.getElementById(`space-${location + 9}`).childNodes[0].className.includes("checker-black")) {
                      if(document.getElementById(`space-${location + 18}`).childNodes[0].nodeName === "DIV") {
                        if(document.getElementById(`space-${location - 7}`).childNodes[0].nodeName === "DIV") {
                          if(document.getElementById(`space-${location - 7}`).childNodes[0].className.includes("checker-black")) {
                            if(document.getElementById(`space-${location - 14}`).childNodes[0].nodeName === "DIV") {
                              alert("Unable to move checker")
                              return
                            }
                            else {
                              this.location = location
                              this.clicked = true
                            }
                          }
                          else {
                            alert("Unable to move checker")
                            return
                          }
                        }
                        else {
                          this.location = location
                          this.clicked = true
                          return
                        }
                      }
                      else {
                        this.location = location
                        this.clicked = true
                        return
                      }
                    }
                    else {
                      alert("Unable to move checker")
                      return
                    }
                  }
                else {
                  this.location = location
                  this.clicked = true
                  return
                }
              }
            }
            else {
              alert("It is red's turn")
              return
            }
          }
        }
      },
      moveChecker(location) {
        console.log(this.clicked)
        if(this.clicked) {
          if(document.getElementById(`space-${location}`).childNodes[0].nodeName === "DIV") {
            alert("Invalid move")
            return
          }
          else {
            if(this.turn === "black") {
              if(this.checkers.find(checker => checker.location === this.location).king) {
                
              }
              else {
                if(this.location + 7 === location) {
                  let index = this.checkers.findIndex(checker => checker.location === this.location)
                  this.checkers[index].location = location
                  this.clicked = false
                  this.turn = "red"
                }
                else if(this.location - 9 === location) {
                  let index = this.checkers.findIndex(checker => checker.location === this.location)
                  this.checkers[index].location = location
                  this.clicked = false
                  this.turn = "red"
                }
                else if(this.location + 14 === location) {
                  if(document.getElementById(`space-${this.location + 7}`).childNodes[0].className.includes("checker-red") && document.getElementById(`space-${this.location + 14}`).childNodes[0].nodeName != "DIV") {
                    let deadIndex = this.checkers.findIndex(checker => checker.location === this.location + 7)
                    let index = this.checkers.findIndex(checker => checker.location === this.location)
                    this.checkers[deadIndex].status = "dead"
                    this.checkers[index].location = location
                    this.clicked = false
                    this.turn = "red"
                  }
                  else {
                    if(window.confirm("Invalid Move click Yes to select another move click No to pass your turn")) {
                      return
                    }
                    else {
                      this.clicked = false
                      this.turn = "red"
                    }
                  }
                }
                else if(this.location - 18 === location) {
                  if(document.getElementById(`space-${this.location - 9}`).childNodes[0].className.includes("checker-red") && document.getElementById(`space-${this.location - 18}`).childNodes[0].nodeName != "DIV") {
                    let deadIndex = this.checkers.findIndex(checker => checker.location === this.location - 9)
                    let index = this.checkers.findIndex(checker => checker.location === this.location)
                    this.checkers[deadIndex].status = "dead"
                    this.checkers[index].location = location
                    this.clicked = false
                    this.turn = "red"
                  }
                  else {
                    if(window.confirm("Invalid Move click Yes to select another move click No to pass your turn")) {
                      return
                    }
                    else {
                      this.clicked = false
                      this.turn = "red"
                    }
                  }
                }
                else {
                  if(window.confirm("Invalid Move click Yes to select another move click No to pass your turn")) {
                    return
                  }
                  else {
                    this.clicked = false
                    this.turn = "red"
                  }
                }
              }
            }
            else {
              if(this.checkers.find(checker => checker.location === this.location).king) {
                
              }
              else {
                console.log("hit")
                if(this.location - 7 === location) {
                  let index = this.checkers.findIndex(checker => checker.location === this.location)
                  this.checkers[index].location = location
                  this.clicked = false
                  this.turn = "black"
                }
                else if(this.location + 9 === location) {
                  let index = this.checkers.findIndex(checker => checker.location === this.location)
                  this.checkers[index].location = location
                  this.clicked = false
                  this.turn = "black"
                }
                else if(this.location - 14 === location) {
                  if(document.getElementById(`space-${this.location - 7}`).childNodes[0].className.includes("checker-black") && document.getElementById(`space-${this.location - 14}`).childNodes[0].nodeName != "DIV") {
                    let deadIndex = this.checkers.findIndex(checker => checker.location === this.location - 7)
                    let index = this.checkers.findIndex(checker => checker.location === this.location)
                    this.checkers[deadIndex].status = "dead"
                    this.checkers[index].location = location
                    this.clicked = false
                    this.turn = "black"
                  }
                  else {
                    if(window.confirm("Invalid Move click Yes to select another move click No to pass your turn")) {
                      return
                    }
                    else {
                      this.clicked = false
                      this.turn = "black"
                    }
                  }
                }
                else if(this.location + 18 === location) {
                  if(document.getElementById(`space-${this.location + 9}`).childNodes[0].className.includes("checker-black") && document.getElementById(`space-${this.location + 18}`).childNodes[0].nodeName != "DIV") {
                    let deadIndex = this.checkers.findIndex(checker => checker.location === this.location + 9)
                    let index = this.checkers.findIndex(checker => checker.location === this.location)
                    this.checkers[deadIndex].status = "dead"
                    this.checkers[index].location = location
                    this.clicked = false
                    this.turn = "black"
                  }
                  else {
                    if(window.confirm("Invalid Move click Yes to select another move click No to pass your turn")) {
                      return
                    }
                    else {
                      this.clicked = false
                      this.turn = "black"
                    }
                  }
                }
                else {
                  if(window.confirm("Invalid Move click Yes to select another move click No to pass your turn")) {
                    return
                  }
                  else {
                    this.clicked = false
                    this.turn = "black"
                  }
                }
              }
            }
          }
        }
        else {
          alert("Please choose a checker to move")
          return
        }
      },
      renderChecker(location) {
        let checker = this.checkers.find(checker => checker.location === location)
        if(checker) {
          return location === checker.location && checker.status === "alive"
        }
        else {
          return false
        }
      }
    },
    computed: {
      deadRedCheckers() {
        return this.checkers.filter(checker => checker.color === "red" && checker.status === "dead")
      },

      deadBlackCheckers() {
        return this.checkers.filter(checker => checker.color === "black" && checker.status === "dead")
      }
    }
  }
</script>

<template>
  <div class="game">
    <div id="red-dead-zone" class="dead-zone">
      <div v-for="checker in deadRedCheckers" :key="checker.id" class="checker checker-red"></div>
    </div>
    <div class="board">
      <div v-for="space in spaces" :key="space.id" :id="space.id" :class="['space', space.className, clicked ? 'space-active' : '']" @click.self="moveChecker(space.location)">
        <div v-if="renderChecker(space.location)" 
        :id="checkers.find(checker => checker.location === space.location).id" 
        :class="['checker', `checker-${checkers.find(checker => checker.location === space.location).color}`, 'checker-alive']" 
        @click="checkMoves(checkers.find(checker => checker.location === space.location).location, 
        checkers.find(checker => checker.location === space.location).color, 
        checkers.find(checker => checker.location === space.location).king)"></div>
      </div>
    </div>
    <div id="black-dead-zone" class="dead-zone">
      <div v-for="checker in deadBlackCheckers" :key="checker.id" class="checker checker-black"></div>
    </div>
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
    align-content: center;
    flex-wrap: wrap;
    width: 17vw;
    height: 56vh;
    background-color: black;
    padding: 10px;
  }

  .dead-zone div {
    margin-right: 10px;
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
    border: 1px solid white;
  }

  .checker-red {
    background-color: red;
  }

  .checker-black {
    background-color: black;
  }

  .space-active:hover {
    cursor: pointer;
  }

  .checker-alive:hover {
    cursor: pointer;
  }
</style>