<template>
    <article class="article">
        <h2>🧑​ Sobre mí</h2>
            <p class="paragraph about__paragraph">
                👋🏼 Hola! me llamo Alejandro Quintero, nací en un pequeño pueblo de Venezuela, mi primer contacto con la programación fué en la universidad con Visual Basic, fué ahí donde me dí cuenta que esto de escribir códigos y lógica se me daban bien.
            </p>
            <p class="paragraph about__paragraph">
                Llegué a España y me propuse estudiar un poco más a fondo algún lenguaje de programación, hasta que decidí irme por los principales lenguajes que conforman una web hoy en día.
            </p>
            <p class="paragraph about__paragraph">
                ¿Mi meta? Tengo varias, pero diría que la principal es llegar a ese punto de la vida en el que pueda decir que amo lo que hago.
            </p>
            <p class="paragraph about__paragraph">
                En mis tiempos libres me gusta cocinar, tomar café, divertirme con algún videojuego y conocer algún rincón del mundo.
            </p>
        <div class="timeline">
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
                            "Diseño y desarrollo de API REST con PHP 8 y Symfony 5.",
                            "Desarrollo de aplicación web consumiendo APIs con AngularJS.",
                            "Soporte y mantenimiento de proyectos internos.",
                            "Implementación de nuevas funcionalidades."
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
                            "Analítica de datos.",
                            "Redactar documentación detallada de los trabajos realizados."
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

p:last-of-type{  
    margin-bottom: 36px;
}

.article{
    max-width: 1100px;
}

.timeline{
    display: flex;
    justify-content: center;
    flex-direction: column;
    align-items: center;
}

@media screen and (min-width: 768px) {

}

@media screen and (min-width: 1400px) {
}

</style>