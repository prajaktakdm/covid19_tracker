<template>
    <div class="text-center">
        <h2 class=" font-weight-bold">{{text}}</h2>
        <div class="mt-4 mb-10 pb-2">
            {{timestamp}}
        </div>
    </div>
</template>

<script>
import moment from 'moment'

export default {
    name:'DataTitle',
    props: ['text','dataDate'],
    computed: {
        timestamp: function(){
            return moment(this.dataDate).format('MMMM Do YYYY,h:mm:ss a')
        }
    },

}
</script>

<style scoped>

</style>