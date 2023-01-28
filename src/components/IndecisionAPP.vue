<template>
  <section id="principal">
    <h1>{{ texto }}</h1> 
    <img v-if="imagen" :src="imagen"> <!-- Cuando haya imagen ser verá !-->
    <div class="indecision-container">
        <input v-model='pregunta' type="text" placeholder="Pregunta de Si y No...">
        <div>
            <h2 class="animate__animated animate__flash">{{ respuesta }}</h2>
        </div>
    </div>
  </section>
</template>

<script>
export default {
    name: 'indecisionApp',
    data(){
        return{
            texto:'Indecision App',
            pregunta:'',
            respuesta: null,
            imagen:null,
        }
    },
    methods:{
        // https://yesno.wtf/#api
        async obtenerRespuesta(){
            this.respuesta = 'Pensando...'
            // const datos = await fetch('https://yesno.wtf/#api').then( respuesta => respuesta.json() )
            // console.log(datos)
            const {answer, image} = await fetch('https://yesno.wtf/api').then( respuesta => respuesta.json() )
            console.log(answer)
            console.log(image)
            this.respuesta = answer
            this.imagen = image
        },
        mayus(){
            //this.cosa = this.cosa.toUpperCase() * cosa a mayuúsculas
            this.texto = this.texto.toUpperCase()
        }
    },
    watch:{ // En /Clases/ hay ejemplo
        pregunta( valor ){
            if( valor.endsWith('?') ){
                 this.obtenerRespuesta()
            }
        }
    },
    mounted(){ // por defecto
        // console.log('Hola mundo')
        //this.cosa() * para no necesitar de un botón
        this.mayus()
        // this.obtenerRespuesta() // Comentar para probar watch
        // console.log(this.texto)
    },

}
</script>

<style>

</style>