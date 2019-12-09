<template>
  <div class="hello">
    <h3>High people</h3>
    <ul class="list">
      <li v-for="(person, index) in highPeopleList" v-bind:key="index" class="list_item">
        <div>
          <div> <span>Nane:</span> {{person.name}} </div> 
          <div> <span>Gender:</span> {{person.gender}}  </div> 
          <div> <span>Heigh:</span> {{person.height}}  </div> 
          <div> <span>Mass:</span> {{person.height}}  </div> 
        </div>
        <div>
          <div>
             <span>Films:</span> 
              <a v-for="(film, index) in person.films" v-bind:key="index" :href=film>
                Film {{index}} 
              </a> 
          </div>
          <div> <span>Skin color:</span> {{person.skin_color}}  </div> 
          <div> <span>Hair color:</span> {{person.hair_color}}  </div> 
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'PeopleList',
  props: {
    height: Number
  },
  data() {
    return {
      peopleList: []
    }
  },
  created() {
    axios
      .get('https://swapi.co/api/people/')
      .then(response => {
        this.peopleList = response.data.results;
      });
  },
  computed: {
    highPeopleList() {
      return this.peopleList.filter(preson => preson.height > this.height);
    }
  }
}
</script>
<style lang="scss">
  .list{
    list-style: none;
    padding: 0;
    margin: 0 auto;
    width: 90%;
    max-width: 800px;
    .list_item {
      display: flex;
      text-align: left;
      border-radius: 20px;
      padding: 20px;
      margin: 10px 0; 
      box-shadow: 0 0 20px rgba(0,0,0,0.2);
      > div {
        flex: 1;
      }
      span{
        font-weight: bolder;
      }
      a {
        text-decoration: none;
        color: #000;
        transition: all .2s ease-in-out;
        &:hover {
          opacity: 0.6;
        }
      }
    }
  } 
</style>

<!-- Add "scoped" attribute to limit CSS to this component only -->
