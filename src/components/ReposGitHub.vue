<template>
    <!-- <div>
        <ul v-for="repo in data">
            <li>{{ repo.name }}</li>
        </ul>
    </div> -->
    <article class="repos">
        <h2 class="grid-item-1">🧑‍💻 Repositorios</h2>
        <div class="container-repos">

        </div>
    </article>
</template>

<script>
    export default{
        name: "ReposGithub",
        data(){
            return {
                data : null
            }
        },
        mounted(){
            fetch('https://api.github.com/users/alejandquintero/repos')
                .then(res => res.json())
                .then(res => {
                    console.log(res)
                    this.data = res

                })
        }
    }

</script>

<style scoped>

.repos{
    max-width: 1100px;
}
.container-repos{
    background-color: azure;
    width: 300px;
    height: 400px;
    border-radius: 15px;
}
</style>