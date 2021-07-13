<template>

  <section class="src-components-final">
    <h1>Final</h1>
    <br />
    <input type="text" v-model="textoAModificar">
    <div v-show="getCantidadInput > 0">
      <b> Cantidad: {{getCantidadInput}} </b><br />
      <b> Codificado: {{codificar()}} </b><br />
      <b> Mayúscula: {{pasarAMayuscula()}} </b><br />
      <b> Minúscula: {{pasarAMinuscula()}} </b><br />
      <b> Mayúscula/Minúscula: {{intercaladoMayusPrimero()}} </b><br />
      <b> Minúscula/Mayúscula: {{intercaladoMinusPrimero()}} </b><br />
    </div>
    <hr />
    <p>
      Respuestas: 1 - A, 2 - B, 3 - C, 4 - B, 5 - B y D
    </p>
  </section>

</template>

<script>

  export default  {
    name: 'src-components-final',
    props: [],
    mounted () {

    },
    data () {
      return {
        textoAModificar: ''
      }
    },
    methods: {
      codificar(){
        let res = this.pasarAMinuscula();
        let arr = res.split('');

        for(let i = 0; i < this.getCantidadInput; i++){
          switch(arr[i]){
            case "a":
              arr.splice(i, 1, "u");
              break;
            case "e":
              arr.splice(i, 1, "o");
              break;
            case "o":
              arr.splice(i, 1, "e");
              break;
            case "u":
              arr.splice(i, 1, "a");
              break;
          }
        }

        res = arr.join('');
        
        return res;
      },
      pasarAMayuscula(){
        return this.textoAModificar.toUpperCase();
      },
      pasarAMinuscula(){
        return this.textoAModificar.toLowerCase();
      },
      intercaladoMinusPrimero(){
        let intercalado = '';

        for(let i = 0; i < this.getCantidadInput; i++){
          if(i % 2){
            intercalado += this.textoAModificar.charAt(i).toUpperCase();
          }else{
            intercalado += this.textoAModificar.charAt(i).toLowerCase();
          }
        }

        return intercalado;
      },
      intercaladoMayusPrimero(){
        let intercalado = '';

        for(let i = 0; i < this.getCantidadInput; i++){
          if(i % 2){
            intercalado += this.textoAModificar.charAt(i).toLowerCase();
          }else{
            intercalado += this.textoAModificar.charAt(i).toUpperCase();
          }
        }

        return intercalado;
      }
    },
    computed: {
      getCantidadInput(){
        return this.textoAModificar.length
      }
    }
}


</script>

<style scoped lang="css">
  .src-components-final {

  }
</style>
