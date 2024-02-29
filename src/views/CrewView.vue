<script>
export default{
    data(){
        return{
            astronauts: [],
            selectedAstronaut: null
        }
    },
    mounted(){
        this.loadAstronautData()
    },
    methods:{
        loadAstronautData(){
            fetch('data.json')
            .then( res => res.json())
            .then(data =>{
                this.astronauts = data.crew

                if(this.astronauts.length > 0){
                    this.selectedAstronaut = this.astronauts[0]
                }
            })
            .catch(err =>{
                console.log('Error Loading Crew')
            })
        },
        showAstronaut(astronaut){
            this.selectedAstronaut = astronaut
        }
    }
}

</script>

<template>
    <main class="crew flex flex-col justify-center items-center gap-4">
        <p>02 Meet your crew</p>
        <div v-if="selectedAstronaut">
            <img :src="selectedAstronaut.images.png" :alt="selectedAstronaut.name" style="max-width: 200px;">
        </div>

        <div class="flex gap-4">
            <div class="button rounded-full" :class="{'active':selectedAstronaut === astronaut}" v-for="astronaut in astronauts" :key="astronaut.name" @click="showAstronaut(astronaut)"></div>
        </div>

        <div class="details flex flex-col justify-center items-center gap-4" v-if="selectedAstronaut">
            <p>{{ selectedAstronaut.role.toUpperCase() }}</p>
            <p>{{ selectedAstronaut.name.toUpperCase() }}</p>

            <p>{{ selectedAstronaut.bio }}</p>
        </div>
    </main>
</template>

<style>
.crew{
    background-image: url(../assets/images/crew/background-crew-desktop.jpg);
}
</style>