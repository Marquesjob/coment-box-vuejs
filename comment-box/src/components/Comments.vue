<template>
    <div class="container w-50 mt-4">
        <h1>Comentários</h1>
        <hr />
       <FormTodo v-on:add-todo="addComment"></FormTodo>
        <div class="list-group">
            <p v-if="comments.length <= 0"><strong>Sem comentários por enquanto =( ...</strong></p>
            <div class="list-group-item" v-for="(comment, index) in allComments">
                <span class="comment__author">Autor: <strong>{{ comment.name }}</strong></span>
                <p>{{ comment.message }}</p>
                <div>
                    <a v-on:click.prevent="deleteComment(index)" href="#" title="Excluir"> Excluir</a>
                </div>
            </div>
        </div>
        <hr />
    </div>
</template>

<script>
    import FormTodo from './FormTodo'
    export default {
    
        components: {
            FormTodo
        },

        data() {  //Referente a banco de dados 
            return {
                comments: [],
                name: '',
                message: ''
            }
        },

        methods: {

            addComment(comment) {
                this.comments.push(comment);
            },

            deleteComment(index) {
                this.comments.splice(index, 1);
            }
        },
        
        computed: { // Referente a interface, clientside.
            allComments() {
                return this.comments.map(comment => ({
                    ...comment,
                    name: comment.name.trim === '' ? 'Anônimo' : comment.name
                }))
            }
        },

        watch: { // observa mudanças em propriedades especificas e aplica um comportamento.

        }
    
    }

</script>

<style>
</style>