<template>
    <article class="timeline" v-for="(job, index) in jobs" :key="index" >
        <div class="year">
            {{ job.startDate }} - {{ job.endDate }}
        </div>
        <div class="job">
            <h4>{{ job.jobTitle }}</h4>
            <h5>{{ job.company }}</h5>
            <ul>
                <li v-for="(item, index) in job.items" :key="index"> {{ item }} </li>
                <li class="container-img">
                    <img v-for="(logo, index) in job.logos" :key="index" :src="logo">
                </li>
            </ul>
        </div>
    </article>
</template>
  
  <script>
      export default{
          name: "Timeline",
          props:{
            jobs : Object          
        }
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

    .container-img{
        display: flex;
        gap: 10px;
        width: 35px;
    }


    .timeline{
        width: 100%;
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
        padding: 2rem 0rem 0rem 2rem;
        width: 70%;
        text-align: left;
    }


  </style>