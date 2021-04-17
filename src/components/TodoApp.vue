<template>
  <div>
    <div class="item-add">
      <input type="textarea" placeholder="Write new task" v-model="newItem" />
      <div @click="addItem">Add new task</div>
      <p>
        New to-do: <span> {{ newItem }} </span>
      </p>
    </div>

    <TodoItem
      v-for="item in items"
      v-bind:key="item.id"
      :item="item"
      @checkClicked="checkItem"
      @removeClicked="removeItem"
    />
  </div>
</template>


<script>
import TodoItem from "./TodoItem.vue";

export default {
  components: {
    TodoItem,
  },
  data() {
    return {
      newItem: "",
      items: [
        { title: "Write your to-do", completed: false, id: 1 }
      ],
    };
  },
  methods: {
    addItem() {
      if(this.newItem != ""){
      this.items.push({
        title: this.newItem,
        completed: false,
        id: Math.random(),
      });
      this.newItem = "";
      }
    },
    checkItem(id) {
      const index = this.items.findIndex((el) => el.id === id);
      this.items[index].completed = true;
    },
    removeItem(id) {
      const index = this.items.findIndex((el) => el.id === id);
      this.items.splice(index, 1);
    }
  },
};
</script>

<style>
.item-add {
  text-align: center;
}
.item-add p {
  font-size: 20px;
}
.item-add p span {
  font-size: 20px;
  font-weight: 600;
}
.item-add input {
  height: 36px;
  max-width: 800px;
  font-size: 28px;
  padding: 10px 15px;
  border: 2px solid #8044C7;
}

.item-add input:focus {
  border: 2px solid #4a2c6e;
  outline: none;
}

.item-add div{
  font-size: 26px;
  border: solid 3px #8044C7;
  background: white;
  color: #8044C7;
  max-width: 200px;
  padding: 10px 20px;
  margin: 20px auto 50px auto;
  transform: scale(1);
}

.item-add div:hover{
  cursor: pointer;
  background: #8044C7;
  color: white;
}

.item-add div:active{
  transform: scale(0.9);
}

.item {
  border: 3px solid #8044C7;
  margin: 10px auto 10px auto;
  padding: 5px;
  text-transform: uppercase;
  max-width: 600px;
  min-height: 60px;
  background: white;
}

.item .check, .item .trash{
  font-size: 30px;
  padding: 10px;
  float: right;
  color: white;
  stroke: #8044C7;
  stroke-width: 25px;
}


.item .check:hover, .item .trash:hover{
  cursor: pointer;
  color:  #8044C7;
}

.item .task{
  font-size: 24px;
  max-width: 20px;
  color: #8044C7;
  padding: 10px 15px;
  margin: auto 0;
}

.item.completed{
  opacity: 0.7;
  text-decoration: line-through;
}
</style>
