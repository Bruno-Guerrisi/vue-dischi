<template>
    <div class="my_container">

        <div class="container">
            <ul >
                <!-- v-if="listDisc !== null" -->
                <li class="col-6 col-md-4 col-lg-2" v-for="(element, i) in listDisc" :key="`element-${i}`">

                    <Card   :url="element.poster"
                            :title="element.title"
                            :author="element.author"
                            :date="element.year"
                            :genre="element.genre"/>
                </li>
            </ul>
            <!-- <div v-else>

            </div> -->
        </div>
    </div>
</template>

<script>
import axios from 'axios';
import Card from "@/components/Card.vue";

export default {
    name : 'Main',
    components: {
        Card,
    },
    data(){
        return{
            listDisc: null,
        }
    },
    created() {

        this.getListDisc();
    },
    methods: {

        getListDisc(){
            axios.get('https://flynn.boolean.careers/exercises/api/array/music')
            .then(result => {

                this.listDisc = result.data.response;
            })
            .catch(error => {
                console.log(error);
            })
        }
    }
    
}
</script>

<style lang="scss" scoped>

    div.my_container{
        display: flex;
        flex-direction: column;
        flex-grow: 1;
        

        div.container{
            ul{
                display: flex;
                flex-wrap: wrap;
                justify-content: center;
                list-style: none;

                li{
                    padding: 5px;
                    margin-bottom: 20px;
                }
            }
        }
    }
</style>