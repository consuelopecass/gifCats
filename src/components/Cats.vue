<template>
    <div>
        <div class="contenedor d-flex">
            <!-- Formulario -->
            <form class="">
                <!-- Titulo para Gif -->
                <div class="">
                    <label for="">Titulo: </label>
                    <input class="" type="text" v-model="titleGif">
                </div>
                <!-- Color de filtro para el Gif -->
                <div class="filtro">
                    <label for="">Filtro: </label>
                        <select @change="cambiarFiltro">
                            <option>Elija un filtro para la imagen</option>
                            <option
                                v-for="filtro in filterStyle"
                                :key="filtro.value"
                                :value="filtro.value"
                                v-text="filtro.filtro"
                            ></option>
                        </select>
                </div>
                <!-- Color para el título  -->
                <div class="color">
                    <label>Color: </label>
                    <select class="select-color" @change="cambiarColor">
                        
                        <option>Elija un color para el título</option>
                        <option
                            v-for="color in fontStyle"
                            :key="color.value"
                            :value="color.value">
                            {{ color.color }}
                        </option>
                    </select>
                    
                </div>
                <div class="circle-color" :style="style"></div>
                <!-- Tamaño de letra título Gif-->
                <div class="tamano">
                    <label for="">Tamaño: </label>
                    <input type="text" v-model="fontSize" />
                </div>
        </form>
    </div>
    <!-- Insertando el gif -->
    <div class="contenedor-gif">
        <div class="center">
            <button @click.prevent="obtenerGatos" class="btn">Obtener mi gato</button>
            <img 
                :src="imageGif" 
                :style="imageStyle"/>
        </div>
        
    </div>
    </div>
</template>


<script>
export default {
name: 'gifcats',
  //props: {},
data () {
    return {
        imageGif: "",
        titleGif: "",
        fontSize: "",
        style: {
            backgroundColor: "white",
        },
        imageStyle: {
            filter: "",
            width: "70%",
            height: "auto"
        },
        titleStyle: {
            color: "",
            fontSize: "30px",
        },
        fontStyle: [
            { color: "Azul", value: "blue" },
            { color: "Rojo", value: "red" },
            { color: "Verde", value: "green" },
            { color: "Amarillo", value: "yellow" },
            { color: "Naranjo", value: "orange" },
        ],
        filterStyle: [
            { filtro: "Sepia", value: "sepia"},
            { filtro: "Invert", value: "invert" },
            { filtro: "Blur", value: "blur" },
            { filtro: "Opacity", value: "opacity" },
            { filtro: "Blanco/Negro", value: "grayscale" },
        ],
    };
},
  //computed: {},
methods:{
obtenerGatos() {
    this.imageGif = `https://cataas.com/cat/gif/says/${this.titleGif}?filter=${this.imageStyle.filter}&color=${this.titleStyle.color}&size=${this.fontSize}&width=300`;
    console.log(this.imageGif);  
}, 
cambiarColor(e){
    this.style.backgroundColor = e.target.value; 
    this.titleStyle.color = e.target.value;
},
cambiarFiltro(e){
    this.imageStyle.filter = e.target.value;
}
  //components: {}
}
};
</script>

<style>
*{
    font-family: Avenir, Helvetica, Arial, sans-serif;
}
label {
    margin: 10px;
    text-align: left;
}
input{
    border: none;
    width: 230px;
    height: 20px;
    margin: 5px 0;
}
select{
    width: 235px;
    height: 23px;
    margin: 5px 0;
}
img{
    padding-top: 30px;
    display: block;
    margin: 0 auto;
}

.center {
    text-align: center;
}
.d-flex {
    display: flex;
    flex-flow: row nowrap;
    justify-content: center;
    align-content: center;
}
.select-color { 
    height: 20px;
}
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    color: #2c3e50;
}
.contenedor {
    background: #50CB93;
    padding: 40px 100px;
}
.circle-color {
    width: 30px;
    height: 30px;
    border-radius: 50%;
    margin: 10px 15px;
    order: 1; 
}
.contenedor-gif{
    background: #ACFFAD;
    text-align: center;
    padding: 20px 30px;
}
.btn {
    border: none; 
    font-size: 18px;
    color: #ACFFAD;
    background: #54436B;
    height: 40px;
    width: 200px;
    display: inline-block;
}
.btn:hover{
    background: #2c3e50;
}
</style>
