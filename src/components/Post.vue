<template>
    <div>
        <h1>Poster un commentaire</h1>

        <form @submit="postData" method="post">
            <input type="text" name="title" v-model="post.title" placeholder="Insérez une titre"> <br>
            <input type="text" name="body" v-model="post.body" placeholder="Insérez un commentaire"> <br>
            <input type="text" name="userId" v-model="post.userId" placeholder="Indiquez votre identifiant"> <br>
            <button type="submit">Postez</button>
        </form>

    </div>
</template>

<script>
export default {
    name: "Post",
    data() {
        return {
            post: {
                title: null,
                body: null,
                userId: null
            }
        }
    },
    methods: {
        async postData(e) {
            console.warn(this.post)
            e.preventDefault();
            fetch('https://jsonplaceholder.typicode.com/posts', {
                method: 'POST',
                body: JSON.stringify({
                    title: this.post.title,
                    body: this.post.body,
                    userId: this.post.userId,
                }),
                headers: {
                    'Content-type': 'application/json; charset=UTF-8',
                },
            })
                .then((response) => response.json())
        }
    }
}
</script>