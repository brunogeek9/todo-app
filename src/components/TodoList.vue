 <template>
  <div>
      <input type="text" class="todo-input" placeholder="o que precisa ser feito ?"
      v-model="newTodo" @keyup.enter="addTodo">
      <!-- lista de coisas para fazer -->
      <div v-for="todo in todos" :key="todo.id" class="todo-item">
          {{todo.title}}
      </div>
      

  </div>
</template>

<script>
export default {
  name: 'Todo List',
  data(){
      return{
          newTodo: '',
          idForTodo: 3,
          todos:[
              {'id': 1,'title':'terminar o tutorial','completed': false},
              {'id': 2,'title':'lavar o resto da roupa','completed': false}
          ]
      }
  },
  methods:{
      addTodo(){
          if(this.newTodo.trim().length == 0){
              return;
          }
          this.todos.push({
              id: this.idForTodo,
              title: this.newTodo,
              completed: false
          });
          this.newTodo = '';
          this.idForTodo++;
      }
  }
}
</script>

<style>
    .todo-input{
        width: 100%;
        padding: 10px 18px;
        font-size: 18px;
        margin-bottom: 10px;
    }
    .todo-item{
        margin-bottom: 12px;
        display: flex;
        align-items: center;
        justify-content: space-between;
    }
</style>
