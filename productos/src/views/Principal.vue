<template>


<body>
    <div id="Princ">
        <Menu></Menu>
        <Producto :ida="2"></Producto>
        <Tarjetas></Tarjetas>
        <PiePagina></PiePagina> 
        
    </div>  
</body>


</template>



  
<script>
// @ is an alias to /src
import Menu from '@/components/Menu.vue'
import PiePagina from '@/components/PiePagina.vue'
import Producto from '@/components/Producto.vue'
import Tarjetas from '@/components/Tarjetas.vue'

export default {
    name: 'Principal',
    components: {
        Menu,
        PiePagina,
        Producto,
        Tarjetas
        
    },
}
</script>

<style>
    .color-box {
        width: 40px;
        height: 40px;
        border-radius: 50%;
        margin: 7px;
        display: inline-block;
    }

    .clic {
        cursor: pointer;
    }

    .quantity button {
        border-radius: 50%;
        display: inline-block;
        width: 30px;
    }

    .quantity div {
        text-align: center;
        min-width: 30px;
        display: inline-block;
        font-weight: bold;
    }

    .buy-box {
        margin: 20px;
    }

    footer {

        text-align: center;
        padding: 30px 10px;
        margin-top: 50px;
        min-height: 100px;
    }

    .container {
        margin-top: 50px;
    }

    .producto-relacionado-precio {
        background: orangered;
        color: white;
        text-align: center;
        padding: 10px;
    }
</style>