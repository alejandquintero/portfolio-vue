<template>
    <article class="article">
      <div class="container-img">
        <img alt="Foto de Alejandro Quintero" class="img-profile" src="@/assets/profile-home.webp"/>
      </div>
      <div class="paragraphs-profile">
        <h1 class="profile-title">Hola<span class="color-dark-blue">.</span><br/> Soy Alejandro</h1>
        <p class="paragraph">🧑‍💻​ Full Stack Developer en <a href="https://www.tigloo.es/" target="_blank" class="relevant color-dark-blue">@Tigloo</a> y 🧑‍🎓 estudiante en <a href="https://www.42madrid.com/" target="_blank" class="relevant color-dark-blue">@42Madrid</a>. Amo el café ☕​, me gusta el Backend y curiosamente me puedo divertir con CSS.😅​.</p>
      </div>
    </article>
</template>

<script>
    export default{
        name: "Profile"
    }
</script>

<style scoped>

.article{
  display: flex;
  justify-content: center;
  flex-direction: column;
  align-items: center;
  max-width: 1200px;
  gap: 60px;
}

.article-tech{
  width: 100%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  gap: 16px;
}

.container-techs{
  display: flex;
  gap: 20px;
  justify-content: flex-start;
}

.container-logos{
  width: 40px;
}

.container-img{
  position: relative;
  min-width: 250px;
  max-width: 300px;
  overflow: hidden;
  border-radius: 50%;
  box-shadow: 0 0 25px #8ca1bf;
  animation: expand-image .8s ;
}

.profile-title{
  font-family: 'Monument';
  color: var(--color-font-dark);
  font-size: 2.5rem;
  margin-bottom: 16px;
}
.subtitle{
  font-family: 'Monument';
  color: var(--color-font-dark);
}

@keyframes expand-image {
  0%{
    transform: scale(0);
  }
  50%{
    transform: scale(1.15);
  }
  100%{
    transform: scale(1);
  }
}

@media screen and (min-width: 768px) {
  
}

@media screen and (min-width: 900px) {
    .article{
        flex-direction: row;
    }

    .container-img{
      max-width: 400px;
    }
    
    .profile-title{
      font-size: 5rem;
      line-height: 100px;
    }
}


@media screen and (min-width: 1400px) {
}

</style>