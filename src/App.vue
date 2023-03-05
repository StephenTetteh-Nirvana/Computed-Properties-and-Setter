<template>
<h2>Fullname-{{firstname}} {{lastname}}</h2>
<button @click="changeName">Set Full Name</button>
<h2>{{ Totalvalue }}</h2>
<button @click="items.push({id:'4',title:'Macbook',price:400})">Add Item</button>
<template v-for="item in items" :key="item.id">
  <h2> {{ item.id }} {{ item.title }} {{ item.price }}</h2>
</template>

</template>

<script>

export default {
  name: 'App',
  data(){
    return{
      firstname: 'Stephen',
      lastname: 'Tetteh',
      items:[
        {
        id:'1',
        title:'Tv',
        price:400
        },
        {
          id:'2',
         title:'phone',
         price:600
        },
        {
        id:'3',
        title:'laptop',
        price:700
        },
      ]
      }
    },
    methods: {
      changeName(){
        this.fullName='Clark Kent'
      }
    },
    computed: {
      fullName:{
        get(){
          return `${this.firstname} ${this.lastname}`
        },
        set(value){
          const names=value.split(' ')
          this.firstname=names[0]
          this.lastname=names[1]
        }
      },
     Totalvalue(){
      return this.items.reduce((total,current) => (total=total + current.price),0)
     },
     HighvalueItems(){
      return this.items.filter(item => item.price > 400) 
     }
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align:center;
  color: #2c3e50;
  margin-top: 60px;
}

</style>
