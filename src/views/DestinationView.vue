<script>
export default{
    data(){
        return{
            getDestination: [],
            selectedDestination: null
        }   
    },
    mounted(){
        this.loadDestination()
    },
    methods:{
        loadDestination(){
            fetch('data.json')
            .then(res => res.json())
            .then(data =>{
                this.getDestination = data.destinations

                if(this.getDestination.length > 0){
                    this.selectedDestination = this.getDestination[0]
                }
            })
            .catch(err =>{
                console.log(err)
            })
        },
        showDestination(destination){
            this.selectedDestination = destination
        }
    }
}

</script>

<template>
    <main class="destination flex flex-col justify-center items-center gap-4">
        <p>01 Pick your destination</p>

        <div v-if="selectedDestination">
            <img :src="selectedDestination.images.png" :alt="selectedDestination.name" style="max-width: 250px">
        </div>

        <div class="planets flex gap-4">
            <p class="li" :class="{'active':selectedDestination === destination}" v-for="destination in getDestination" :key="destination.name" @click="showDestination(destination)">{{ destination.name }}</p>
        </div>

        <div class="details flex flex-col justify-center items-center gap-4" v-if="selectedDestination">
        <h1>{{ selectedDestination.name }}</h1>
        <p>{{ selectedDestination.description }}</p>

        <hr>

        <div class="avg_dist flex flex-wrap justify-center item-center gap-10">
            <div>
                <p>AVG. DISTANCE</p>
                <h2>{{ selectedDestination.distance }}</h2>
            </div>
            
            <div>
                <p>EST. TIME TRAVEL</p>
            <h2>{{ selectedDestination.travel }}</h2>
            </div>
        </div>
        
        </div>
    </main>
</template>

<style>
.destination{
    background-image: url(../assets/images/destination/background-destination-desktop.jpg);
}

.avg_dist{
    width: 100%;
    text-align: center;
}

@media only screen and (max-width: 800px) {
    .destination{
      background-image: url(../assets/images/destination/background-destination-tablet.jpg);
    }
  }
  
  @media only screen and (max-width: 500px) {
    .destination{
      background-image: url(../assets/images/destination/background-destination-mobile.jpg);
    }
  }
</style>