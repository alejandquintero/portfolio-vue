<script>
// import { RouterLink, RouterView } from 'vue-router'
import Profile from './components/Profile.vue'
import NavigationBar from './components/NavigationBar.vue'
import Timeline from './components/Timeline.vue'
import AboutMe from './components/AboutMe.vue'
import ReposGitHub from './components/ReposGitHub.vue'

export default{
  name : "App",
  components : {
    Profile,
    NavigationBar,
    Timeline,
    AboutMe,
    ReposGitHub
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
        <AboutMe></AboutMe>
      </section>
      
      <section class="section section-3" id="contact">
        <ReposGitHub></ReposGitHub>
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
  min-height: 100vh;
  justify-content: center;
  align-items: center;
  padding: 24px;
  color: var(--color-font-dark);
  font-family: 'Geomanist';
  background-color: var(--color-bg-dark) ;
}

.color-dark-blue{
  color: var(--color-bg-dark-blue);
}

.section-2{
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: center;
}

.section:not(#home){
  padding-top: 88px;
}

.paragraph{
  font-family: 'Geomanist';
  font-size: 1.2rem;
  color: var(--color-font-dark-text-paragraph);
}

.relevant{
  display: inline-flex;
  font-weight: bold;
  position: relative;
  transition: transform .2s ease-in-out;
  justify-content: center;
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
