<template>
    <div>        
        <footer v-bind:style="'background-color:' + footerColor">
        </footer>
    </div>
</template>

<script>
    export default {
        name:'PiePagina',
        props: {

        },
        data() {
            return {
                footerColor: "slategrey",
            }
        },
    }
</script>
