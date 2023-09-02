<template>
    <div @click="menuActive" class="container__icon__menu" v-if="renderBurger"> 
        <i class="icon__menu" :class="iconStyle"></i>
    </div>
    <nav :class="{ navActive: menu }" @click="navActive" >       
        <ul>
            <li v-for="(item, index) in listItems" :key="index">
            <a :href="item.ref"><span class="color-dark-blue"> { </span>{{  item.text }}<span class="color-dark-blue"> }</span></a>
            </li>
        </ul>
    </nav>
</template>

<script>

export default{
    name: "NavigationBar",
    data(){
        return{
            menu: false,
            renderBurger : false,
            viewportWidth : null,
            listItems : 
            [
                {
                    text: 'alejandro',
                    ref: '#home' 
                },
                {
                    text: 'sobre mí',
                    ref: '#about-me' 
                },
                {
                    text: 'repositorios',
                    ref: '#repos' 
                },
                {
                    text: 'contacto',
                    ref : '#contact'
                }
            ]
        }
    },
    created() {
        this.viewportWidth = window.innerWidth
        window.addEventListener("resize", this.eventResize);
    },
    destroyed() {
        window.removeEventListener("resize", this.eventResize);
    },
    mounted(){
        if(window.innerWidth >= 768 ){
            this.renderBurger = false;
            this.menu = true
        }else{
            this.renderBurger = true
        }

    }, 
    methods: {
      menuActive(){
        this.menu = !this.menu;
      },
      navActive(){
        if(this.renderBurger){
            this.menu = false;
        }
      },
      eventResize(e){
        this.viewportWidth = window.innerWidth;
      }
    },
    computed:{
      iconStyle(){
        return !this.menu ? '' : 'icon__menu--active';
      }
    },
    watch:{
        viewportWidth(oldValue, newValue){
            if(newValue != null && newValue >= 768){
               this.renderBurger = false;
               this.menu = true;
              }else{
               this.renderBurger = true;
               this.menu = false;
            }
        }
    }
}

</script>

<style scoped>

nav{
    font-family: 'Monument';
    color: #fff;
    font-size: .8rem;
    letter-spacing: 1px;
    padding: 24px;
    position: fixed;
    top: 0;
    z-index: 10;
    width: 100%;
    height: 100vh;
    background-color: var(--color-bg-dark);
    transform: translateX(-200vw);
    transition: transform .4s;
}

ul{
    display: flex;
    flex-direction: column;
    justify-content: space-evenly;
    align-items: center;
    height: 100%;
    list-style: none;
    padding: 0;
    gap: 10px;
}

ul:first-child{
    right: 0;
}

a{
    text-decoration: none;
    color: var(--color-font-dark)
}

li{
    display: flex;
    justify-content: center;
    width: max-content;
}

li::before{
  content: '';
  position: absolute;
  bottom: -3px;
  margin: auto;
  background-color: var(--color-font-dark);
  width: 0%;
  height: 2px;
  transition: width .2s ease-in-out;
}

li:hover::before{
  width: 100%;
}

.container__icon__menu{
  display: flex;
  position: fixed;
  right: 1.5rem;
  justify-content: center;
  align-items: center;
  padding: 10px 2px;
  width: 2.5rem;
  height: 3rem;
  cursor: pointer;
  z-index: 30;
}


.navActive{
  transform: translateY(0);
}

.icon__menu{
  position: relative;
  display:block;
  width: 100%;
  height: 5px;
  border-radius: 5px;
  background-color: #7e5430;
}

.icon__menu::before, 
.icon__menu::after{
  content: '';
  display: block;
  background-color: #eba73c;
  position: absolute;
  top: 10px;
  border-radius: 5px;
  width: 100%;
  height: 5px;
  transition : all .2s;
}

.icon__menu::after{
  top: -10px
}

.icon__menu--active{
    height: 0;
}

.icon__menu--active::before,
.icon__menu--active::after{
  top: 0;
  transform: rotate(45deg)
}

.icon__menu--active::after{
  transform: rotate(-45deg)
}

@media screen and (min-width: 768px) {
    nav{
        height: auto;
        transform: translateX();
    }

    ul{
        flex-direction: row;
    }

}
</style>