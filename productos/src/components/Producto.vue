<template>
    <div class="Producto">
        

        
        <div class="row">
            <h3>{{items.nombre}}</h3>
        </div>
        <div class="row">
            <div class="col-12 col-sm-6 col-md-4 ">
                <img :src="items.imagen"
                    alt="" width="350">
            </div>
            <div class="col-12 col-sm-6  col-md-8">
                <h6 v-html="items.descripcion"></h6>
                <div class="p-3 mb-2 text-white" v-bind:style="precioEstilos">
                    Precio: {{items.precio}} BOB 
                </div>
                <h5>Color</h5>
                <div > 
                    <div v-for="color in items.colores" class="color-box clic" :style="'background:' + color" v-on:click="pedido.color = color"></div>

                </div>
                <h5>Cantidad</h5>
                <div class="quantity">
                    <button v-if="contador > 0" v-on:click="contador -= 1">-</button> <div>{{contador}}</div> <button v-on:click="contador += 1">+</button>
                </div>
                <div class="buy-box">                                                   
                    <button type="button" class="btn btn-primary" v-if="contador > 0 & pedido.color !== null" v-on:click="pedido.cantidad = contador, pedido.id = items.id, enviar()" >Comprar</button>
                </div>
               
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Producto',
    data() {
        const api = process.env.VUE_APP_API;
        return{
            api,
            items: [],
            precioEstilos: "background: orangered; color: white; font-weight: bold",
            contador: 0,
            pedido: {
                id: null,
                cantidad: 0,
                color:null
            }

        }
    },

    methods: {
        getItems() {
            this.axios({
                method: 'get',
                url: this.api + '/Productos/1'
            })
                .then((response) => {
                    this.items = response.data;
                    console.log(response);
                    console.log(items);
                    
                })
                .catch((error) => { console.log(error) })
                .finally(() => { });
        },
        enviar(){
                    alert(`
                        id= ${this.pedido.id}, 
                        cantidad = ${this.pedido.cantidad}, 
                        color = ${this.pedido.color}` );

                },
    },
    mounted() {
        this.getItems();
    },
}
</script>