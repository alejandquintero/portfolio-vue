<template>
    <article class="article">
        <h2 class="grid-item-1">🧑​ Sobre mí</h2>
        <div class="grid-item-2 container-img-about">
            <img src="@/assets/profile-about.webp" alt="Foto de Alejandro">
        </div>
        <div class="grid-item-3 container-about-paragraph">
            <p class="paragraph about__paragraph">
                👋🏼 ¡Hola! Me llamo Alejandro, actualmente Full Stack Developer con Symfony y AngularJS, me gusta mucho más el Backend y VueJs💚. Soy estudiante de 42 Madrid 🤍, donde, además de aprender, escribir mucho código y divertirme, voy encontrando mi lugar en este mundo.
            </p>
            <p class="paragraph about__paragraph">
                Día a día me esfuerzo en crecer y en dar lo mejor de mí, poco a poco voy cumpliendo mis sueños, me gusta lo simple, pero no lo convencional, y, cuando se me presentan retos, no me da miedo enfrentarlos.
            </p>
            <p class="paragraph about__paragraph">
                ¿Mi meta? Tengo varias, pero diría que la principal es llegar a ese punto de la vida en el que pueda decir que soy muy feliz.
            </p>
            <p class="paragraph about__paragraph">
                En mis tiempos libres me gusta cocinar, tomar café, divertirme con algún videojuego y conocer algún rincón del mundo.
            </p>
        </div>
        <div class="grid-item-4 timeline">
            <h3>🕛💻 Timeline</h3>
            <Timeline :jobs="jobs"></Timeline>
        </div>
    </article>
</template>

<script>
    import Timeline from './Timeline.vue';
    export default{
        name: "AboutMe",
        components:{
            Timeline
        },
        data(){
            return {
                jobs : 
                [
                    {
                        startDate : "2022",
                        endDate: "Ahora",
                        jobTitle : "Full Stack Developer",
                        company : "Tigloo",
                        items: [
                            "Diseño y desarrollos de API REST con PHP 8 y Symfony 5.",
                            "Desarrollo de aplicaciones webs.",
                            "Automatización de tareas.",
                            "Soporte, mantenimiento e implementacion de nuevas funcionalidades en los proyectos.",
                        ],
                        logos: [
                            "logos/symfony.svg",
                            "logos/angularjs.svg",
                            "logos/mysql.svg",
                            "logos/php.svg",
                            "logos/javascript.svg",
                        ]
                    },
                    {
                        startDate : "2021",
                        endDate: "2022",
                        jobTitle : "SQL Developer",
                        company : "Oracls Development",
                        items: [
                            "Estructuración y modelado de datos.",
                            "Redactar documentación para los procesos implementados en las BBDD.",
                            "Desarrollo de querys, functions, scripts, views, stored procedures y triggers de acuerdo a las necesidades de las aplicaciones.",
                            "Diseñar, crear e implementar nuevas arquitecturas de BBDD de acuerdo con los requerimientos funcionales y de desarrollo",
                            "Diseñar y mantener los diferentes esquemas y objetos de la base de datos asegurando su estabilidad, rendimiento y fiabilidad.",
                            "Redactar documentación detallada de los trabajos realizados."
                        ],
                        logos: [
                            "logos/mysql.svg",
                            "logos/php.svg",
                        ]
                    }
                ]      
            }
        }
    }

</script>

<style scoped>

h2{
    text-align: center;
    margin-bottom: 36px;
    font-family: 'Monument';
    color: var(--color-font-dark);
    letter-spacing: 2px;

}

h3{
    text-align: left;
    display: block;;
    margin-bottom: 36px;
    font-family: 'Monument';
    letter-spacing: 2px;
}

p{
    margin-bottom: 16px;
    text-align: justify;
}

/* p:last-of-type{  
    margin-bottom: 44px;
} */

.article{
    max-width: 1100px;
    display: grid;
    grid-template-columns: 200px;
    grid-template-rows: 16px;
    column-gap: 64px;
    row-gap: 64px;
    justify-items: center;
    /*el shorthand es gap*/
}
.container-img-about{
    width: 300px;
    height: 300px;
    border-radius: 50%;
    overflow: hidden;
    box-shadow: 0 0 15px #8ca1bf;
}

.timeline{
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
}

.grid-item-1{
    grid-column: 1 / 3;
    grid-row: 1;
}

.grid-item-2{
    grid-column: 1 / 3;
    grid-row: 2;
}

.grid-item-3{
    grid-column: 1 / 3;
    grid-row: 3;
}

.grid-item-4{
    grid-column: 1 / 3;
    grid-row: 4;
}

@media screen and (min-width: 768px) {
    .article{
        grid-template-columns: 300px 1fr;
        grid-template-rows: 16px;

    };

    .grid-item-1{
    grid-column: 1 / 3;
    grid-row: 1;
    }

    .grid-item-2{
        grid-column: 1 / 2;
        grid-row: 2;
    }

    .grid-item-3{
        grid-column: 2 / 3;
        grid-row: 2;
    }

    .grid-item-4{
        grid-column: 1 / 3;
        grid-row: 3;
    }
}

@media screen and (min-width: 1400px) {
}

</style>