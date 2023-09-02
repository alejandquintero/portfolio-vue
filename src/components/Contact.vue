<template>
    <article class="article">
        <h2 class="grid-item-1">📧📞Contacto</h2>
        <form v-on:submit.prevent="onSubmit">
        
            <label for="name">
                <span>Nombre:</span>
                <input type="text" id="name" :class="{ error : errorName}" v-model="name">
                <span class="spanError" v-if="errorName">Debes introducir un nombre</span>
            </label>
            
            <label for="email">
                <span>Email:</span>
                <input type="email" id="email" :class="{ error : errorEmail}" v-model="email" >
                <span class="spanError" v-if="errorEmail">Verifica si el email introducido tiene un formato válido</span>
            </label>

            <label for="message">
                <span>Mensaje:</span>
                <textarea id="message" :class="{ error : errorMessage}" v-model="message"></textarea>
                <span class="spanError" v-if="errorMessage">Debes introducir un mensaje</span>
            </label>
            
            <Transition appear mode="out-in" name="fade">

                <div class="container-button-icons-contact" v-if="!showMessageSubmit">
                        
                    <button type="submit" v-on:click="send()">
                        Enviar
                    </button>            

                    <div class="container-icons" > 
                        <IconsContact></IconsContact>
                    </div>

                </div>

                <label v-else="showMessageSubmit" class="message-form" :class="{ red: !successSubmit }">
                    {{ statusMsg }}
                </label>

            </Transition>

        </form>
    </article>
</template>

<script>
    import IconsContact from './IconsContact.vue';
    export default{
        name: "Contact",
        components:{
            IconsContact
        },
        data(){
            return {
                name: '',
                email : '',
                message: '',
                errorName : false,
                errorEmail : false,
                errorMessage : false,
                successSubmit : false,
                showMessageSubmit : false,
                statusMsg : '',
                endpoint: 'https://formspree.io/f/xjvdebkn'
            }
        },
        methods: {
            send(){

                !this.name.length > 0 ? this.errorName = true : this.errorName = false;
                    
                !this.message.length > 0 ? this.errorMessage = true : this.errorMessage = false;
                
                !this.validateEmail(this.email) ? this.errorEmail = true : this.errorEmail = false;

                console.log(this.validateEmail(this.email))
                    
                if(!this.errorName && !this.errorMessage && !this.errorEmail){

                    let headers = new Headers();
                    headers.append("Accept", `application/json`);
    
    
                    let form = {
                        name: this.name,
                        email: this.email,
                        message: this.message,
                        subject : `${this.name} te ha enviado un mensaje a través de tu web Alejandro`,
                    };
    
                    let body = JSON.stringify(form)
    
                    let requestOptions = {
                        method: 'POST',
                        body,
                        headers
                    }
                    
                    console.log(requestOptions)
    
                    fetch(this.endpoint, requestOptions)
                        .then(res => res.json())
                        .then(data => {
                         
                            if( data && data.ok == true){
                                this.name = this.email = this.message = ''
                                this.statusMsg = 'Gracias por dejar tu mensaje, pronto me pondré en contacto contigo 😊';
                                this.successSubmit = true;
                            }else{
                                this.statusMsg = 'Algo ha ido mal al enviar tu mensaje 😥, por favor, inténtalo de nuevo mas tarde';
                                this.successSubmit = false;
                            }
                            
                        })
                        .catch(error => {
                            this.statusMsg = 'Algo ha ido mal al enviar tu mensaje 😥, por favor, inténtalo de nuevo mas tarde';
                            this.successSubmit = false;
                        })
                        .finally(() => {
                            this.showMessageSubmit = true;

                            setTimeout(() => {
                                this.showMessageSubmit = false;
                            }, 8000)


                        })
                }else{
                    console.log('Error en formulario')
                }
            
            },
            validateEmail(email){
                const emailRegex = /^(([^<>()\[\]\\.,:\s@"]+(\.[^<>()\[\]\\.,:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/

                if(emailRegex.test(email)) {
                    return true
                }else{
                    return false
                } 
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

.article{
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    width: 100%;
    max-width: 1100px;
}

form{
    display: flex;
    flex-direction: column;
    width: 100%;
    max-width: 500px;
    gap: 2.2rem;
}

label{
    display: flex;
    flex-direction: column;
    width: 100%;
    gap: 1rem;
    position: relative;
}

input,
textarea{
    height: 40px;
    border-radius: 10px;
    padding: 1rem;
    border: none;  
    background-color: var(--color-font-dark);
    box-shadow: 0 0 10px #8ca1bf;
}

input:focus,
textarea:focus{
    outline: none;
    box-shadow: 0 0 10px var(--color-bg-dark-blue);
}

textarea{
    min-height: 200px;
    resize: none;
}

button{
    width: 100%;
    height: 40px;
    border-radius: 10px;
    border: none;
    cursor: pointer;
    box-shadow: 0 0 10px #8ca1bf;
    background-color: var(--color-bg-dark-blue);
    transition: background .2s;
}
.container-button-icons-contact{
    display: flex;
    flex-direction: column;
    gap: 2.2rem;
}

.message-form{
    width: 100%;
    /* height: 50px; */
    text-align: center;
    padding: 2rem;
    border-radius: 10px;
    background-color: #9fdeaf;
    box-shadow: 0 0 10px #8ca1bf;
    color: var(--color-bg-dark);
}

.red{
    background-color: #ff7a6b;
}

.spanError{
    position: absolute;
    font-size: 14px;
    bottom: -28px;
}

button:hover{
    background-color: #9fdeaf;
}

.error{
    box-shadow: 0 0 10px #ff7a6b;
}
.error:focus{
    box-shadow: 0 0 10px #ff7a6b;
}
.container-icons{
    display: flex;
    justify-content: space-evenly;
    /* width: 100%; */
    gap: 10px;
}


@media screen and (min-width: 768px) {
}

@media screen and (min-width: 1400px) {
}

</style>