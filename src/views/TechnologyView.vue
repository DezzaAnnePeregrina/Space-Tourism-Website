<script>
export default{
    data(){
        return{
            getTechnologies: [],
            selectedTechnologies: null
        }
    },
    mounted(){
        this.loadTechnologies()
    },
    methods:{
        loadTechnologies(){
            fetch('data.json')
            .then(res => res.json())
            .then(data =>{
                this.getTechnologies = data.technology

                if(this.getTechnologies.length > 0){
                    this.selectedTechnologies = this.getTechnologies[0]
                }
            })
            .catch(err =>{
                console.log(err)
            })
        },
        showTechnology(technology){
            this.selectedTechnologies = technology
        }
    }
}

</script>

<template>
    <main class="technology flex flex-col justify-center items-center gap-4">
        <p>03 Space launch 101</p>

        <div v-if="selectedTechnologies">
            <img :src="selectedTechnologies.images.portrait" :alt="selectedTechnologies.name" style="max-width: 300px;">
        </div>

        <div class="flex gap-4">
            <div class="button rounded-full" style="color:black" :class="{'active':selectedTechnologies === technology}" v-for="technology in getTechnologies" :key="technology.name" @click="showTechnology(technology)">{{ technology.num }}</div>
        </div>
        
        <div class="intro" v-if="selectedTechnologies">
            <h2>{{selectedTechnologies.name}}</h2>
            <p>{{selectedTechnologies.description}}</p>
        </div>
    </main>
</template>



<style>
.technology{
    background-image: url(../assets/images/technology/background-technology-desktop.jpg);
}
</style>