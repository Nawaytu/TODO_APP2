<template>
    <div>
          <ul class="list-group mt-3">
            <li class="list-group-item" v-for="(todo, index) in todos" :key="index">
                <div class="row">
                    <div class="col">
                        <span v-if="todo.isDone">
                            <del>{{ todo.activity }}</del>
                        </span>
                        <span v-else>{{ todo.activity }}</span>
                    </div>
                    <div class="col-auto">
                        <div class="row gx-2">
                            <div class="col">
                                <button @click="deleteTODO(index)" class="btn btn-danger">Delete</button>
                            </div>
                            <div class="col">
                                <button @click="done(index)" class="btn btn-primary">Done</button>
                            </div>
                        </div>
                    </div>
                </div>
            </li>
          </ul>
        </div>
</template>

<script>
export default{
    setup(props, {emit}){
        const deleteTODO = index => {
           emit('deleteTodo', index); 
        }

        const done = index => {
            emit('doneTodo', index)
        }

        return { deleteTODO, done}
    },
    props: {
        todos:{
            type: Array,
            default: []
        }
    },
}
</script>