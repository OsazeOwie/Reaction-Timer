<template>
  <p>Reaction Time: {{score/1000}} s</p>
  <p> {{rank}}</p>
   <button @click="toggleTable">Show Rank Table</button>
  <div class="rankTable" v-if="showRanks">
      <ol>
          <h2>Ranks</h2>
          <li>Fingers of Oz!!! 🏎💨🥇 <br> <span>(0.4s and less)</span></li>
          <li>Sharp Guy! 🏍💨🥈 <br><span> (0.4s - 0.8s)</span></li>
          <li>Try they fast 😂🐢 <br><span> (anything less)</span></li>
      </ol>
  </div>
</template>

<script>
export default {
    props: ["score"],
    data() {
        return {
            rank: null,
            showRanks: false
        }
    },
    mounted() {
        if(this.score < 400){
            this.rank = "Fingers of Oz!!! 🏎💨🥇"
        } else if(this.score < 800){
            this.rank = "Sharp Guy! 🏍💨🥈"
        } else {
            this.rank = "Try they fast 😂🐢"
        }
    },
    methods: {
        toggleTable() {
            this.showRanks = !this.showRanks
        }
    }
}
</script>

<style scoped>
button {
    background-color: seagreen;
    color: white;
    border-radius: 10px;
    border: 1px solid springgreen;
    padding: .5em .7em;
}
.rankTable {
    margin: 30px auto;
    display: flex;
    flex-direction: column;
    text-align: left;
    width: fit-content;
    border-radius: 20px;
    border: 1px solid springgreen;
    background-color: seagreen;
    color: white;
    padding: .2em 1em;
    
}
.rankTable h2 {
    margin: 20px;
    text-decoration: underline;
}
.rankTable li {
    margin-bottom: 30px;
}
span {
    color: rgb(173, 233, 203)
}

p {
    font-weight: 600;
}

</style>