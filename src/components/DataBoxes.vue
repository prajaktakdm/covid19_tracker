<template>
<div class="container">


    <div class="row d-flex justify-content-center">
        <!-- Box-1 -->
        <div class="cases col-sm-5  shadow-sm p-3 m-2 rounded">
            <h3 class="	font-size-1.875rem line-height-2.25rem font-bold ">Cases</h3>

            <div class="mb-2 text-dark">
                <span class="font-bold">New:</span>
                {{numberWithCommas(stats.NewConfirmed)}}
            </div>
            <div class="mb-4 text-dark">
                <span class="font-bold">Total:</span>
                {{numberWithCommas(stats.TotalConfirmed)}}
            </div>
        </div>

        <!-- Box-2 -->
        <div class="cases col-sm-5  shadow-sm p-3 m-2 rounded">
            <h3 class="font-bold ">Deaths</h3>

            <div class="mb-2 text-dark">
                <span class="font-bold">New:</span>
                {{numberWithCommas(stats.NewDeaths)}}
            </div>
            <div class="mb-4 text-dark">
                <span class="font-bold">Total:</span>
                {{numberWithCommas(stats.TotalDeaths)}}
            </div>
        </div>
    </div>
</div>
</template>


<script>
export default {
   name: 'Databoxes',
   props: ['stats'] ,

   methods: {
       numberWithCommas(x){
           return x.toString().replace(/\B(?=(\d{3})+(?!\d))/g,',')
       }
   }
}
</script>

<style scoped>
.grid{
    display: grid;
    grid-template-columns: auto auto;
    grid-column-gap: 50px;
    grid-row-gap: 10px;
    
}
.cases{
    background: #cae2f1;
    padding-top: 10px;
    text-align: center;
    color: #08438c;
    font-weight: bold;
    
}
</style>