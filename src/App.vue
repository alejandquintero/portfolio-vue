<script>
import { RouterLink, RouterView } from 'vue-router'
import Profile from './components/Profile.vue'
import NavigationBar from './components/NavigationBar.vue'

export default{
  name : "App",
  components : {
    Profile,
    NavigationBar
  },
  data(){
    return{
    }
  }
}

</script>

<template>

  <Transition appear name="fade">
    <div class="container-content">
      <NavigationBar></NavigationBar>

      <section class="section" id="home">
        <Profile></Profile>
      </section>
    
      <section class="section section-2" id="about-me">
        <h2>Section 2</h2>
      </section>
      
      <section class="section section-3" id="contact">
        <h2>Section 3</h2>
      </section>
    </div>
  </Transition>



</template>

<style>

h1{
  margin: 0;
}

section{
  display: flex;
  height: 100vh;
  justify-content: center;
  align-items: center;
  padding: 24px;
  /* background-image: linear-gradient(90deg, #2B4263 25%, #20252c 25%);
  background-image: linear-gradient(90deg, #8CA1BF 25%, #314D73 25%); */
  /* background-image: linear-gradient(90deg, var(--color-bg-dark-blue), var(--color-bg-dark)); */
  background-color: var(--color-bg-dark) ;
}
/* 
.container-content{
   padding: 24px;
} */

.color-dark-blue{
  color: var(--color-bg-dark-blue);
}

/* .section-2,
.section-3{
  background-image: none;
}

.section-2{
  background-color: var(--color-bg-dark-blue) ;
}

.section-3{
  background-color: var(--color-bg-dark) ;
} */

.paragraph{
  font-family: 'Geomanist';
  font-size: 1.2rem;
  color: var(--color-font-dark);
  color: #b3b3b3;
}

.relevant{
  display: inline-flex;
  font-weight: bold;
  position: relative;
  transition: transform .2s ease-in-out;
  justify-content: center;
  /* color: var(--color-font-dark) */
}

.relevant::before{
  content: '';
  position: absolute;
  bottom: -3px;
  margin: auto;
  background-color: var(--color-font-dark);
  width: 0%;
  height: 2px;
  transition: width .2s ease-in-out;
}

.relevant:hover{
 transform: translateY(-5px);
}

.relevant:hover::before{
  width: 100%;
}

</style>
