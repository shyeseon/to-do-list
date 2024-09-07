<script setup>
import { ref, onMounted} from 'vue';
const count = ref(0);

const increase = () => {
  count.value++;
};
const decrement = () => {
  count.value--;
};

const inputValue = ref('');
console.log(inputValue.value);

const handleChange = (event) =>{
  const nextValue = event.target.value;
  inputValue.value= nextValue;
  console.log(inputValue.value);
}

const deletebtn =(index) => {
  todoList.value.splice(index,1);

}
const todoList= ref([
                    {text :'vue'    , done : false} ,
                    {text :'react'  , done : false},
                    {text :'vercel' , done : false}
                    ])
const checkbtn =() =>{
  todoList.value.push(inputValue.value);
  console.log(todoList.value);
}

/**
  todo item{
    text:string,
    done:boolean,

  }
*/
</script>

<template>

  <h1>Todo List</h1>
  <h6>{{todoList}}</h6>
  <div>
    <div>count: {{ count }}</div>
    <button @click="increase">+</button>
    <button @click="decrement">-</button>
  </div>
  <input @change = "handleChange"/>
  
  <button @click="checkbtn">확인</button>

  <div class="Todo-item mt-2" v-for="(item,index) in todoList" >
    <input type="checkbox" v-model="item.done"/>
    <span :class="{'done-item' : item.done}" >{{item.text}}</span>
    <div>
    <button class="btn btn-sm btn-secondary">수정</button>
    <button class="btn btn-sm btn-danger" @click="deletebtn">삭제</button>
    </div>
  </div>
</template>

<style scoped>
h1 {
  color: red;
}
.Todo-item {
  display: flex;
  width: 100%;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;

}
.done-item{
  text-decoration:line-through;
}
</style>
