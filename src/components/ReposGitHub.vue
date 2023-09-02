<template>
    <article class="repos">
        <h2 class="grid-item-1">🧑‍💻 Repositorios</h2>
        <div class="container-repos" v-if="!loading">
            <a class="repo" v-for="repo in repos" :href=repo.url target="_blank">
                <div>
                    <h3>{{ repo.name  }}</h3>
                    <p>{{ repo.description  }}</p>
                </div>
                <p class="languages">
                    <span class="language" v-for="(language, key) in repo.languages">
                        <i :class="key"></i>
                        {{  key  }}
                    </span>
                </p>
            </a>
        </div>

        <div class="container-repos" v-if="loading">
            <a class="repo container-skeleton" v-for="item in itemsSkeleton">
                <div class="container-info-skeleton">
                    <h3 class="skeleton"></h3>
                    <p class="skeleton"></p>
                    <p class="skeleton"></p>
                </div>
                <p class="container-languages-skeleton">
                    <i class="skeleton"></i>
                    <span class="skeleton"></span>
                </p>
            </a>
        </div>

    </article>
</template>

<script>

export default {
    name: "ReposGithub",
    data() {
        return {
            repos: null,
            itemsSkeleton : 12,
            loading: true
        }
    },
    mounted() {
        if (!sessionStorage.getItem('data')) {
            fetch('https://api.github.com/users/alejandquintero/repos')
                .then(res => res.json())
                .then(repos => {

                    const getReposData = async (repos) => {

                        let c = 0;
                        let reposData = new Array();

                        for (let i = 0; i < repos.length; i++) {
                            await getDataLanguagesFromGitHub(repos[i].name)
                                .then(languages => {
                                    let values =
                                    {
                                        id: repos[i].id,
                                        name: repos[i].name,
                                        description: null,
                                        languages,
                                        url: repos[i].svn_url
                                    }
                                    reposData[c] = values;
                                });
                            await getDataDescriptionFromGitHub(repos[i].name)
                                .then(description => {
                                    reposData[c].description = description;
                                    c++;
                                });
                        }

                        return reposData;

                    }

                    const getDataLanguagesFromGitHub = async (repoName) => {
                        let data = await fetch(`https://api.github.com/repos/alejandquintero/${repoName}/languages`)
                            .then(res => res.json())
                            .then(languages => {
                                return languages;
                            })

                        return data;
                    }

                    const getDataDescriptionFromGitHub = async (repoName) => {
                        let data = await fetch(`https://api.github.com/repos/alejandquintero/${repoName}`)
                            .then(res => res.json())
                            .then(repo => {
                                return repo.description;
                            })

                        return data;
                    }

                    getReposData(repos).then(repos =>{
                        //console.log(repos);
                        this.repos = repos.filter(repo => repo.name !=='alejandquintero')
                        this.loading = false;
                    });

                })
        }
    }
}

</script>

<style scoped>

h2{
    font-family: 'Monument';
    color: var(--color-font-dark);
    letter-spacing: 2px;
}
.repos {
    max-width: 1100px;
    display: flex;
    gap: 32px;
    flex-direction: column;
    justify-content: center;
    align-items: center;
}

.container-repos {
    display: grid;
    grid-template-columns: repeat(1, minmax(300px, 400px));
    gap: 30px;

}

.repo{
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    background-color: var(--color-font-dark);
    padding: 16px;
    color: var(--color-bg-dark);
    font-weight: bolder;
    border-radius: 20px;
    height: 200px;
    transition: transform .2s;
    box-shadow: 0 0 10px #8ca1bf;
}

.repo:hover{
    transform: scale(1.1);
    cursor: pointer;
    box-shadow: 0 0 10px var(--color-bg-dark-blue);

}

h3{
    margin-bottom: 12px;
    color: #4c6a94;
}
.languages{
    display: flex;
    gap: 8px;
}

.language{
    display: flex;
    justify-content: flex-start;
    align-items: center;
    position: relative;
    gap: 5px;
}

i{
    width: 10px;
    height: 10px;
    background-color: #f1e05a;
    border-radius: 50%;
}

p{
    text-align: justify;
}

.container-info-skeleton {
    display: flex;
    flex-direction: column;
}
.container-info-skeleton > h3, 
.container-info-skeleton > p{
    width: 50%;
    height: 16px;
    border-radius: 10px;
}

.container-info-skeleton > p{
    margin-bottom: 12px;
    width: 80%;
}

.container-info-skeleton > p:last-child{
    width: 60%;
}

.container-languages-skeleton{
    display: flex;
    align-items: center;
}
.container-languages-skeleton > span{
    width: 15%;
    height: 16px;
    position: relative;
    transform: translateX(5px);
    border-radius: 10px;
}
.container-languages-skeleton > i{
    width: 10px;
    height: 10px;
    border-radius: 50%;
}
.HTML{
    background-color: #e34c26;
}
.JavaScript{
    background-color: #f1e05a;
}
.CSS{
    background-color: #563d7c;
}
.PHP{
    background-color: #4f5d95;
}
.Shell{
    background-color: #89e051;
}
.Twig{
    background-color: #c1d026;
}
.Hack{
    background-color: #878787;
}
.Vue{
    background-color: #41b883;
}
.Dockerfile{
    background-color: #384d54;
}

.skeleton{
    animation: skeleton-loading 1s linear infinite alternate;
}
.container-skeleton{
    cursor: auto;
    transform: scale(1);
}

.container-skeleton:hover{
    transform: scale(1);
    cursor: auto;
}

@keyframes skeleton-loading {
    0%{
        background-color: #b9b9b9;
    }
    100%{
        background-color: #989898;
    }
}

@media screen and (min-width: 768px) {
    .container-repos{
        grid-template-columns: repeat(2, minmax(300px, 400px));
    }
}

@media screen and (min-width: 1040px) {
    .container-repos{
        grid-template-columns: repeat(3, minmax(300px, 400px));
    }
}
</style>