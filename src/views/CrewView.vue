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
    <main class="crew flex flex-col">
        <div class="flex gap-1">
            <div class="button" :class="{'active':selectedAstronaut === astronaut}" v-for="astronaut in astronauts" :key="astronaut.name" @click="showAstronaut(astronaut)"></div>
        </div>

        <div v-if="selectedAstronaut">
            <h2>{{ selectedAstronaut.name }}</h2>
            <img :src="selectedAstronaut.images.png" :alt="selectedAstronaut.name" style="max-width: 200px;">
        </div>
        
    </main>
</template>

<style>
.crew{
    background-image: url(../assets/images/crew/background-crew-desktop.jpg);
}

.button{
    background-color: gray;
    width: 20px;
    height: 20px;
}

.button.active{
    background-color: antiquewhite;
}
</style>