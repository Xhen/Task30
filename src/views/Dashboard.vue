<template>
  <div class="dashboard">

    <div class="person-wrap">
      <Person
      :key="currentPerson.id"
      :name="currentPerson.name"
      :title="currentPerson.title"
      :img="currentPerson.img"
      :gender="currentPerson.gender"
      />
    </div>

    <div class="btn-list">
      <button class="btn" @click="handleChoice(1)">Yes</button>
      <button class="btn" @click="handleChoice(0)">Nope</button>
    </div>

    <div class="list-wrap">

      <ul >
          <b>Like list</b>
        <li v-for="p in this.likedList" :key="p.id">
          {{ p.name }}
        </li>
      </ul>

        <ul >
          <b>Dislike list</b>
        <li v-for="p in this.dislikedList" :key="p.id">
          {{ p.name }}
        </li>
      </ul>

    </div>
    
  </div>
</template>

<script>
// @ is an alias to /src
import Person from '@/components/Person.vue'
import axios from 'axios'

export default {
  name: 'dashboard',
  components: {
    Person
  },
  data: function() {
    return {
      index: 0,
      currentPerson: {},
      likedList: [],
      dislikedList: [],
      personList: [
      {
          "id":0,
          "title":"Direct Tactics Administrator",
          "name":"Gabriel",
          "img":"https://robohash.org/grew.png?size=300x300",
          "gender":"male"
      },
      {
          "id":1,
          "title":"National Infrastructure Supervisor",
          "name":"Marcellus",
          "img":"https://robohash.org/through.png?size=300x300",
          "gender":"female"
      },
      {
          "id":2,
          "title":"Product Data Strategist",
          "name":"Clyde",
          "img":"https://robohash.org/suggest.png?size=300x300",
          "gender":"female"
      },
      {
          "id":3,
          "title":"International Accounts Orchestrator",
          "name":"Dean",
          "img":"https://robohash.org/voluptatem.png?size=300x300",
          "gender":"male"
      },
      {
          "id":3,
          "title":"Corporate Quality Consultant",
          "name":"Oscar",
          "img":"https://robohash.org/cry.png?size=300x300",
          "gender":"male"
      },
      {
          "id":4,
          "title":"Internal Markets Coordinator",
          "name":"Glenna",
          "img":"https://robohash.org/lot.png?size=300x300",
          "gender":"female"
      },
      {
          "id":5,
          "title":"Regional Group Specialist",
          "name":"Brandyn",
          "img":"https://robohash.org/eight.png?size=300x300",
          "gender":"female"
      },
      {
          "id":6,
          "title":"Legacy Creative Agent",
          "name":"Otis",
          "img":"https://robohash.org/et.png?size=300x300",
          "gender":"male"
      },
      {
          "id":7,
          "title":"Investor Configuration Representative",
          "name":"Celestine",
          "img":"https://robohash.org/range.png?size=300x300",
          "gender":"female"
      },
      {
          "id":8,
          "title":"Customer Interactions Analyst",
          "name":"Gwendolyn",
          "img":"https://robohash.org/eveniet.png?size=300x300",
          "gender":"male"
      },
      {
          "id":9,
          "title":"Investor Configuration Representative",
          "name":"Celestine",
          "img":"https://robohash.org/range.png?size=300x300",
          "gender":"female"
      },
      {
          "id":10,
          "title":"Customer Donkey Analyst",
          "name":"Gwendolyn",
          "img":"https://robohash.org/eveniet.png?size=300x300",
          "gender":"male"
      },
      {
          "id":11,
          "title":"God",
          "name":"Craig",
          "img":"https://proxy.duckduckgo.com/iu/?u=https%3A%2F%2Fi1.rgstatic.net%2Fii%2Fprofile.image%2F280090295455745-1443790138550_Q512%2FCraig_Marais.jpg&f=1",
          "gender":"Deity"
      }
    ]
    }
  },
  created: function() {
    this.fetchData();
    this.getCurrentPerson();
  },
  methods: {

    fetchData: function() {
      let vm = this;
      axios({
        method: "post",
        url: "https://app.fakejson.com/q",
        data: this.payload
      }).then(function(resp) {
        console.log(resp.data);
      });
    },

    handleChoice: function(boolean) {
      console.log(boolean);
      // If person likes 
      if(boolean) {
        this.likedList.push(this.currentPerson);
        } else {
        this.dislikedList.push(this.currentPerson);
      }
      this.increment();

      if(this.index > this.personList.length) {
        alert("No more delicious people to look at, but hey there is a list of people you judged based on their looks.");
      } else {
        this.getCurrentPerson();
      }
    },

    getCurrentPerson: function() {
      this.currentPerson = this.personList.filter(e => e.id == this.index)[0];
    },
    increment: function() {
      this.index++
    }
  }
}
</script>
<style lang="sass">

.dashboard
  font-family: 'Roboto'
  text-transform: capitalize

.btn-list
  display: flex
  justify-content: center

.btn
  padding: 12px
  outline: 0
  border: 0
  margin: 10px
  border-radius: 10px
  width: 100px

  &:nth-child(even)
    background: red
  &:nth-child(odd)
    background: LawnGreen

.list-wrap
  display: flex
  flex-flow: row nowrap
  width: 350px
  margin: 0 auto
  border: 1px solid black

.list-wrap > ul
  list-style: none
  flex: 1
  text-align: center
</style>
