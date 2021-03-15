<template>

  <div>  
    <div class="item" 
    v-bind:class="{completed: item.completed}" >
      <span class="task">{{ item.title }}</span>
      <span class="trash" @click="removeItem"><font-awesome-icon icon="trash" /></span>
      <span class="check" v-if="!item.completed" @click="checkItem"><font-awesome-icon icon="check" /></span>
    </div>
    <font-awesome-icon icon="arrow-up" />
    <font-awesome-icon icon="arrow-down" />
  </div>

</template>

<script>
export default {
    props: ['item'],
    methods: {
        checkItem(){
           this.$emit('checkClicked', this.item.id) 
        },
        removeItem(){
           this.$emit('removeClicked', this.item.id) 
        }
    }
}
</script>
