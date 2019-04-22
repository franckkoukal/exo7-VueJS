<template>
    <div class="col-xs-12 col-sm-6">
        <p v-if="!server">Merci de selectionner un serveur</p>
        <p v-else>Server #{{server.id}} selected, Status: {{server.status}}</p>
        <hr>
        <button @click="resetStatus">Revenir à Normal</button>
    </div>

</template>

<script>
import {serverBus} from '../../main';

export default {
    data : function() {
        return {
            server: null
        }
    },
    methods:{
        resetStatus(){
            this.server.status =  'Normal';
        }
    },
    created(){
        serverBus.$on('serverSelected', (server) => {
            this.server = server;
        });
    }
}
</script>

<style>

</style>
