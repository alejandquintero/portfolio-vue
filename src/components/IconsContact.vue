<template>

    <div class="container-icon-contact" v-for="icon in icons">
        <a :href="icon.href" target="_blank">
            <img :src="icon.img" class="img-contact" :alt="icon.alt">
        </a>
    </div>

</template>

<script>
    export default{
        name: "IconsContact",
        data(){
            return{
                icons : [
                    {
                        href: 'http://www.linkedin.com/in/alejandroquinteroe',
                        img : 'logos/linkedin.webp',
                        alt : 'LinkedIn icon'
                    },
                    {
                        href: 'https://github.com/alejandquintero',
                        img : 'logos/github.webp',
                        alt : 'GitHub icon'
                    },  
                    {
                        href: 'mailto:alejandquinteroe@gmail.com',
                        img : 'logos/email.webp',
                        alt : 'Email icon'
                    }, 
                    {
                        href: 'tel:602547908',
                        img : 'logos/phone.webp',
                        alt : 'Phone icon'
                    }
                ]

            }
        }
    }

</script>

<style scoped>

.container-icon-contact{
    width: 30px;
    height: 30px;
    transition: transform .2s;
}

.img-contact{
    filter: invert(1) brightness(.8);
}
.container-icon-contact:hover{
    transform: scale(1.5);
    filter: drop-shadow(0px 0px 5px var(--color-bg-dark-blue));
}
</style>