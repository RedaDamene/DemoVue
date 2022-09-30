<template>
    <div>
        <h1>Liste des postes</h1>
        <table style="display: inline-flex;">
            <tr style="padding: 10px 20px 10px 10px;">UserId</tr>
            <tr style="padding: 10px 20px 10px 10px;">Titre</tr>
            <tr style="padding: 10px 20px 10px 10px;">Commentaire</tr>
            <tr>Action</tr>
        </table>
        <table v-for="post in posts" :key="post.id">
            <tr>{{post.userId}}</tr>
            <tr>{{post.title}}</tr>
            <tr>{{post.body}}</tr>
            <tr><button v-on:click="deletePost">Supprimer</button></tr>
        </table>
    </div>
</template>
<script>
const API_URL = `https://jsonplaceholder.typicode.com/posts/`
export default {
    name: "PostsList",
    data() {
        return {
            posts: null
        }
    },
    mounted() {
        this.fetchData()
    },
    methods: {
        async fetchData() {
            const url = `${API_URL}`
            this.posts = await (await fetch(url)).json()
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