<template>
    <div>

        <form @submit="getComments(this.comments.userId)" method="post">
            <input type="text" name="userId" v-model="comments.userId" placeholder="Indiquez votre identifiant"> <br>
            <button type="submit">Afficher</button>
        </form>

        <h1>Liste des commentaires de l'utilisateur </h1>
        <table style="display: inline-flex;">
            <tr style="padding: 10px 20px 10px 10px;">UserId</tr>
            <tr>Action</tr>
        </table>
        <table v-for="comment in comments" :key="comment.id">
            <tr>{{comment.userId}}</tr>
            <tr><button v-on:click="deletPost">Supprimer</button></tr>
        </table>
    </div>
</template>
<script>
const API_URL = `https://jsonplaceholder.typicode.com/posts/`
const API_URL_COMMENTS = `https://jsonplaceholder.typicode.com/posts?userId=`
export default {
    name: "Comments",
    data() {
        return {
            comments: null
        }
    },
    mounted() {
        this.getComments()
    },
    methods: {
        async getComments(id) {
            const url = `${API_URL_COMMENTS}`
            this.comments = await (await fetch(url + id)).json()
                .then((json) => console.log(json));
        },
        async deletePost(id) {
            const url = `${API_URL}`
            fetch(url + id, {
                method: 'DELETE',
            })
                .then((response) => response.json())
                .then((json) => console.log(json))
        }
    }
}

</script>

<style scoped>

</style>