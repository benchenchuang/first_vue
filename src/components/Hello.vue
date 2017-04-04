<template>
  <div class="hello" id='hello'>
    <h1 v-text="title"></h1>
    <input v-model='newItem'v-on:keyup.enter='addItem'/>
    <ul>
      <li v-for='item in items' v-bind:class={isFinished:item.isFinished} v-on:click='toggleFinish(item)'>
      {{item.babel}}
      </li>
    </ul>
  </div>
</template>

<script>
export default{
  data:function(){
    return{
      title:'this is add title',
      items:[
        {
          babel:'babel one',
          isFinished:false
        },
        {
          babel:'babel two',
          isFinished:true
        }
      ],
      newItem:''
    }
  },
  methods:{
    toggleFinish:function(item){
      item.isFinished=!item.isFinished;
    },
    addItem:function(){
      this.items.push({
        babel:this.newItem,
        isFinished:false
      })
      this.newItem=''
    }
  }
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
.isFinished{
  color:red;
}
ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
