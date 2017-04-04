<template>
  <div id="app">
    <h1 v-text='title'></h1>
    <input v-model='newItem' v-on:keyup.enter='addNew'/>
    <ul>
      <li v-for='item in items' v-bind:class="{finished:item.isFinished}" v-on:click='toggleFinish(item)'>
        {{item.label}}
      </li>
    </ul>
    <h2 v-text='msg'></h2>
  </div>
</template>

<script>
export default {
  data:function(){
    return {
      title:'This is a todo list',
      msg:'this is a msg',
      items: [
        {
          label:'coding',
          isFinished:false
        },
        {
          label:'waking',
          isFinished:true
        },
      ],
      newItem:''
    }
  },
  methods: {
     toggleFinish:function(item){
        item.isFinished = !item.isFinished
      },
      addNew:function(){
        console.log(this.newItem);
        this.items.push({
          label:this.newItem,
          isFinished:false
        })
        this.newItem = '';
      }
  }
}
</script>

<style>
.finished{
  text-decoration:underline;
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
