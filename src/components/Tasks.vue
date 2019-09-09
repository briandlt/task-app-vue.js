<template>
    <div class="container">
        <h3 class="mb-4">{{title}}</h3>
        <form action="" class="form-inline my-4" v-on:submit="addTask">
            <div class="m-auto">
                <input type="text" name="" v-model="tasks.title" class="form-control">
                <input type="submit" value="Agregar" class="btn btn-success mx-2">
            </div>
        </form>
        <table class="table col-sm-8 offset-sm-2">
            <thead>
                <tr>
                    <th>Hecho!</th>
                    <th>Tarea</th>
                    <th>Eliminar</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="task in tasks">
                    <td>
                        <input type="checkbox" name="hecho" id="hecho" v-model="task.done" checked>
                    </td>
                    <td>
                        <span :class="{taskDone: task.done}">{{task.name}}</span>
                    </td>
                    <td><input type="button" value="Eliminar" class="btn btn-danger" v-on:click="deleteTask(task)"></td>
                </tr>
            </tbody>
        </table>
    </div>
</template>

<script>
export default {
    name: 'tasks',
    data() {
        return {
            title: "TASK APP",
            tasks:[
                {
                    name: 'Correr',
                    done: true
                },
                {
                    name: 'Comer',
                    done: false
                },
                {
                    name: 'Lavar',
                    done: false
                },
                {
                    name: 'Leer ',
                    done: false
                }
            ]
        } 
    },
    methods: {
        addTask: function(e){
            e.preventDefault();
            this.tasks.push({
                name: this.tasks.title,
                done: false
            });
            this.tasks.title = "";
        },
        deleteTask: function(task){
            this.tasks.splice(this.tasks.indexOf(task), 1);
        }
    },

}
</script>

<style scope="">
    .taskDone{
        text-decoration: line-through;
    }
</style>