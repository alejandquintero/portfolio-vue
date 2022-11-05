<template>

    <nav>
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
                    text: 'contacto',
                    ref : '#contact'
                }
            ]
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
    background-color: var(--color-bg-dark);
}

ul{
    justify-content: space-evenly;
    display: flex;
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
    
</style>