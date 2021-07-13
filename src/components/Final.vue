<template>

  <section class="src-components-final">
    <h1>Final</h1>
    <br />
    <input type="text" v-model="textoAModificar">
    <div v-show="getCantidadInput > 0">
      <label> Cantidad: {{getCantidadInput}} </label><br />
      <label> Codificado: {{codificar()}} </label><br />
      <label> Mayúscula: {{pasarAMayuscula()}} </label><br />
      <label> Minúscula: {{pasarAMinuscula()}} </label><br />
      <label> Mayúscula/Minúscula: {{intercaladoMayusPrimero()}} </label><br />
      <label> Minúscula/Mayúscula: {{intercaladoMinusPrimero()}} </label><br />
    </div>
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
