<template>
   <div class="mx-auto container">

     <form @submit.prevent="add(text)" class="flex justify-center m-4">
       <input v-model="text" type="text" class="border-black border-2 border-solid">
     </form>

   <article class="container mx-auto max-w-md text-center font-mono">
     <h1 class="text-bold">Todos</h1>
     <ul class="text-white p-0">
       <li v-for="t in todos" :key="t.id" class="flex p-2 items-center list-reset my-2 py-4 bg-orange border-black border-dashed border-2">
        <span @dblclick="toggle(t)" class="flex-1 cursor-pointer" :class="{ 'line-through text-grey-darkest': t.done }">{{t.text}}</span>
        <button @click.once="remove(t)" class="self-end"><img src="https://icon.now.sh/delete/fff" class="h-6"></button>
       </li>
       </ul>
     </article>
     </div>
</template>

<script>
import { mapMutations, mapState, mapActions } from 'vuex';
import { init } from './shared';

export default {
  fetch: init,
  data() {
    return {
      text: ""
    }
  },
  computed: {
    ...mapState({
      todos: state => state.todos
    })
  },
  methods: {
    ...mapActions([
      'add',
      'remove',
      'toggle'
      ])
  }
}
</script>
