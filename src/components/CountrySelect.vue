<template>
    <select 
        @change="onChange"
        v-model="selected" 
        class="form-select block w-full p-3 rounded mt-10"
    >
        <option value="0">Select Country</option>
        <option 
            v-for="country,index in countries"
            :key="index" 
            :value="country.ID"
        >
            {{country.Country}}
        </option>
    </select>
</template>

<script>
export default {
    name: 'CountrySelect',
    props: ['countries'],
    
    data() {
        return {
            selected: 0
        }
    },
    methods: {
        onChange() {
            const country = this.countries.find((item) => item.ID === this.selected)
            this.$emit('get-country', country)
        }
    }
}
</script>
