<template>
    <select v-model="selected" @change="onChange()" 
        class="form-select mt-10 block w-full border">
         <option value="0">Select Country</option>
         <option v-for="(country, index) in countries" :value="country.ID" :key="index">
             {{country.Country}}
         </option>
    </select>
       
</template>

<script>
export default {
    name:'CountrySelect',
    props:['countries'],

    data(){
        return {
            selected:0
        }
    },

    methods:{
        onChange(){
            const country = this.countries.find((item)=>item.ID === this.selected)
            this.$emit('get-country',country)
        }
    }
}
</script>