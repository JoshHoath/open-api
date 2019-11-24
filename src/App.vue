<template>
    <div id="app">
        <div class="container text-center">
            <button id="btn" class="btn btn-danger" v-on:click="compare"><h2>Compare</h2></button>
        </div>
        <div class="group container text-center data-container">
            <button id="btn" class="btn  btb-large btn-primary" v-on:click="getData"><h2>Find a home!</h2></button>
            <div v-if="loading">
            <!-- <img src="../src/assets/loader.gif"/> -->
            <h3>Loading.....</h3>
            </div>

            <div class="wrapper contianer">
                <div class="row">
                    <div class="picture-container" v-for="(group, index) in groups" :key="index">
                        <h3>{{ group.name }} - {{ price }}</h3>
                        <div class="overlay">
                            <a :href="group.imgUrl"><img :src="group.imgUrl" /></a>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import axios from 'axios';
export default {
    name: 'app',
        data () {
            return {
                groups: [], //community
                homes: [],  // homes
                auburnHomes: [],
                bownessHomes: [],
                brentwoodHomes: [],
                eauclairdHomes: [],
                mahoganyHomes: [],
                mountviewHomes: [],
                northwestHomes: [],
                oakridgeHomes: [],
                varsityHomes: [],
                bownessId: '56e20c00-805b-44b7-831f-f33e50edd54e',
                varistyId: "20244d9f-8147-4633-9b29-4c0ec5a762a9",
                mountviewId: "af2c8ca7-e3bb-4c8f-8f40-1f6156f4d7c4",
                auburnId: "1f161dcd-1221-4b0f-9ced-1498807cca55",
                setonId:  "1f161dcd-1221-4b0f-9ced-1498807cca55",
                eauclaireId: "1f161dcd-1221-4b0f-9ced-1498807cca55",
                oakridgeId: "a75e7343-23f3-45c4-a1a4-e88746b11ebf",
                mahoganyId: "84666941-c1b9-43a8-82a0-dbc3a82862c4",
                brentwoodId: "29c7292d-c04b-49c4-acd6-a1a8de952408",
                northwestId: "86b42a15-1a35-4819-8646-6719ea275ecf",
                loading: false,
                firstUrl: "https://a18fda49-215e-47d1-9dc6-c6136a04a33a.mock.pstmn.io/communities",
                secondUrl: "https://a18fda49-215e-47d1-9dc6-c6136a04a33a.mock.pstmn.io/homes"
            }
        },
        methods: {
            getData: function() {
                this.loading = true;
                axios.get(this.firstUrl)
                    .then((response) => {
                        //groups array
                        this.loading = false;
                        this.groups = response.data;
                        this.groupsId = this.groups.map(obj => {
                            if(obj.hasOwnProperty('id'))
                            return obj.id;
                        })
                    }, (error) => {
                        this.loading = false;
                    })
                axios.get(this.secondUrl)
                    .then((response) => {
                        //homes array
                        this.homes = response.data;
                        this.homeGroups = this.homes.map(obj => {
                            if(obj.hasOwnProperty('communityId'))
                            return obj.communityId;
                        })
                    }), (error) => {
                        alert('prices');
                    }

            },
            getNames: function(item, index) {
                    this.groupsforEach()
                    this.homesForEach()

            },
            compare: function() {
                for(this.home in this.homes){
                    if(homes.id === this.auburnId) {
                        this.auburnHomes.push();
                    } else if (this.homes.id === this.bownessId){
                        this.bownessHomes.push();
                    } else if (this.homes.id === this.brentwoodId ){
                        this.brentwoodHomes.push();
                    } else if (this.homes.id === this.eauclaireId ) {
                        this.eauclairdHomes.push();
                    } else if (this.homes.id === this.mahoganyId ) {
                        this.mahoganyHomes.push();
                    } else if (this.homes.id === this.mountviewId ) {
                        this.mountviewHomes.push();
                    } else if (this,homes.id === this.northwestId) {
                        this.northwestHomes.push();
                    } else if(this.homes.id === this.oakridgeId) {
                        this.oakridgeHomes.push();
                    } else if(this.homes.id === this.varsityId) {
                        this.varsityHomes.push();
                    }
                }
            }
            // compare: function(groupId, homeGroups) {
            //     groupId.forEach((e1)=>homeGroups.foreach((e2)=>{
            //         if(e1 === e2){
            //             this.sameId.push(e1)
            //         }
            //     }
            // ));
            // }
        }
    }


</script>

<style lang="scss">
body{
    background-color: black;
    color: white;
}
.data-container {
    width: 85%;
}
.picture-container {
    width: 100%;
    margin-top: 2rem;
    margin-bottom: 5rem;
    .overlay{
      opacity: 1;
      filter: alpha(opacity=100);
    }
    .overlay:hover{
      opacity: 0.3;
      filter: alpha(opacity=30);
    }
    img {
        width: 100%;
        height: 100%;
    }
}
</style>
