<template>
 <div>
  <div>Jugadores</div>
  <ul v-for="(player, i) in players" :key="i">
    <li :class="{'player-turn': player == turn}">
      {{player}}
    </li>
  </ul>
  <div class="wrapper">
    <div class="grid-container">
      <template v-for="(row, i) in map" :key="i">
        <template v-for="(col, j) in row" :key="j">
          <div class="grid-item" @click="select(i,j)">
            <img v-if="map[i][j]" :src="avatar(map[i][j])" width="90">
          </div> 
        </template>
    </template>
    </div>
  </div>
 </div>
</template>

<script>
export default {
  data: () => ({
    map: [
      ['asdac123fsd23', null, null],
      [null, null, null],
      [null, null, '2312xascwe52323'],
    ],
    players: [
      'asdac123fsd23',
      '2312xascwe52323'
    ],
    turn: 'asdac123fsd23'
  }),
  methods: {
    select (x, y) {
      if(this.map[x][y] == null) {
        this.map[x][y] = this.turn
      }
    },
    avatar (name) {
      return `https://avatars.dicebear.com/4.5/api/bottts/${name}.svg`
    }
  }
}
</script>

<style>
  .wrapper {
    display: grid;
    align-items: center;
    justify-items: center;
  }

  .grid-container {
    display: grid;
    grid-template-columns: repeat(3, minmax(100px, 100px));
    justify-items: center;
    align-items: center;
    grid-column-gap: 20px;
    grid-row-gap: 15px;
  }

  .grid-item {
    background: rgb(240, 157, 93);
    text-align: center;
    border: rgb(89, 89, 89) 3px solid;
    width: 100px;
    height: 100px;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .player-turn {
    color: brown;
  }
</style>