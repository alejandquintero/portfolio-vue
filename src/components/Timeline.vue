<template>
    <article class="timeline">
        <div class="year">
            <!-- {{ data.dStart }} - {{ data.dEnd }} -->
            2022 - Ahora
        </div>
        <div class="job">
            <h4>Full Stack Developer</h4>
            <h5>Tigloo</h5>
            <ul>
                <li>
                   Diseño y desarrollo de API REST con PHP 8 y Symfony 5.
                </li>
                <li>
                   Desarrollo de aplicación web consumiendo APIs con AngularJS.
                </li>
                <li>
                   Soporte y mantenimiento de proyectos internos.
                </li>
                <li>
                    Implementación de nuevas funcionalidades.
                </li>
            </ul>
        </div>
    </article>
    <article class="timeline">
        <div class="year">
            2022 - Ahora
        </div>
        <div class="job">
            <h4>Full Stack Developer</h4>
            <h5>Tigloo</h5>
            <ul>
                <li>
                   Diseño y desarrollo de API REST con PHP 8 y Symfony 5.
                </li>
                <li>
                   Desarrollo de aplicación web consumiendo APIs con AngularJS.
                </li>
            </ul>
        </div>
    </article>
    <article class="timeline">
        <div class="year">
            2022 - Ahora
        </div>
        <div class="job">
            <h4>Full Stack Developer</h4>
            <h5>Tigloo</h5>
            <ul>
                <li>
                   Diseño y desarrollo de API REST con PHP 8 y Symfony 5.
                </li>
            </ul>
        </div>
    </article>
</template>
  
  <script>
      export default{
          name: "Timeline"
          
      }
  </script>
  
  <style scoped>

    h4,
    h5{
        margin: 0;
        padding: 0;
    }

    h5{
        font-weight: normal;
        margin-bottom: 14px;
    }

    ul{
        padding: 0 0 0 0rem;
        list-style: none;
    }

    li{
        margin-bottom: 16px;
    }


    .timeline{
        width: 800px;
        font-family: 'Geomanist';
        font-size: 1.2rem;
        color: var(--color-font-dark-text-paragraph);
        display: flex;
        justify-content: center;
    }

    .year{
        display: flex;
        justify-content: flex-end;
        align-items: flex-start;
        position: relative;
        width: 30%;
        text-align: right;
        border-right: 1px solid #d9d9d986;
        padding: 2rem 2rem 2rem 0;
        font-weight: bolder;
    }

    .year::after{
        content: '';
        position: absolute;
        width: 20px;
        height: 20px;
        border-radius: 50%;
        transform: translateX(10px);
        right: 0;
        background-color: var(--color-bg-dark-blue);
    }


    .job{
        display: flex;
        flex-direction: column;
        justify-content: flex-start;
        gap: 5px;
        padding: 2rem 0rem 2rem 2rem;
        width: 70%;
        text-align: left;
    }


  </style>