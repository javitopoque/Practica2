<template>
    <div>
        <div class="container ">

            <div class="row">
                <h4>Productos relacionados</h4>
                </div>
                <div class="row">
                    <div class="col" v-for="item in items">
                        <div class="card" style="width: 18rem; ">
                            <div class="card-body">
                                <h5 class="card-title">{{item.nombre}}</h5>
                                <img :src="item.imagen " v-on:click="counter += 1"
                            alt="" width="250">
                                <p class="card-text">{{ item.descripcion }}</p>
                                    <div class="producto-relacionado-precio">Precio:{{item.precio}} BOB</div>
                                <div>
                        <div>
                            <div v-for="color in item.colores" class="color-box" :style="'background:' + color"></div>
                        </div>
                                </div>
                            </div>
                        </div>
                    </div>



            </div>

        </div>
    </div>
</template>


<script>
export default {
    name: 'Terjetas',
    data() {
        const api = process.env.VUE_APP_API;

        return{
            api,
            items: [],
            toSearch: "?id=2&id=3&id=4",

        }
    },
    methods: {
        getItems() {
            this.axios({
                method: 'get',
                url: this.api + '/Productos/'+this.toSearch
            })
                .then((response) => {
                    this.items = response.data;
                    console.log(response);
                    console.log(items);
                    
                })
                .catch((error) => { console.log(error) })
                .finally(() => { });
        },
    },
    mounted() {
        this.getItems();
    },
}
</script>