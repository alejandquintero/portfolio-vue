<template>
    <article class="article">
      <div class="container-img">
        <img alt="Foto de Alejandro Quintero" class="img-profile" src="@/assets/cuadrado-profile-dark.webp"/>
      </div>
      <div class="paragraphs-profile">
        <h1 class="profile-title">Hola<span class="color-dark-blue">.</span><br/> Soy Alejandro</h1>
        <p class="paragraph">ð§âð»â Full Stack Developer actualmente en <a href="https://www.tigloo.es/" target="_blank" class="relevant color-dark-blue">@Tigloo.</a> Amo el cafÃ© ââ, me inclino hacia el Backend y curiosamente me gusta el CSS ðâ.</p>
      </div>
    </article>
</template>

<script>
    export default{
        name: "Profile",
        data(){
            return {
                data : [
                  'logos/css.webp',
                  'logos/html.webp',
                  'logos/js.webp',
                  'logos/mysql.webp',
                  'logos/php.webp',
                  'logos/vscode.svg'
                ]
            }
        }
    }
</script>

<style scoped>

.article{
  display: flex;
  justify-content: center;
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
  max-width: 400px;
  overflow: hidden;
  border-radius: 50%;
  box-shadow: 0 0 25px #8ca1bf;
  animation: expand-image .8s ;
}

.profile-title{
  font-family: 'Monument';
  color: var(--color-font-dark);
  font-size: 2rem;
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
    .article{
        flex-direction: row;
    }
    
    .profile-title{
      font-size: 5rem;
      line-height: 100px;
    }
}

@media screen and (min-width: 1400px) {
    .profile-title{
        /* line-height: 100px;
        font-size: 5rem; */
    }
}

</style>