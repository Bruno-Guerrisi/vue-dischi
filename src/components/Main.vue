<template>
    <div class="my_container">

        <div v-if="listCard !== null" class="container ">
            <ul>
                
                <li class="col-6 col-md-4 col-lg-2" v-for="(element, i) in listCard" :key="`element-${i}`">

                    <Card   :url="element.poster"
                            :title="element.title"
                            :author="element.author"
                            :date="element.year"
                            :genre="element.genre"/>
                </li>
            </ul>
        </div>

        <div v-else class="container loading">
            <div class="loading-box"></div>
            <span>Loading...</span>
        </div>
    </div>
</template>

<script>
/* import axios from 'axios'; */
import Card from "@/components/Card.vue";

export default {
    name : 'Main',
    components: {
        Card,
    },
    props: {

        listCard: Array,
    },
    /* data(){
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
    } */
    
}
</script>

<style lang="scss" scoped>

    div.my_container{
        display: flex;
        flex-direction: column;
        flex-grow: 1;
        
        div.container.loading{
            display: flex;
            flex-direction: column;
            align-items: center;
            height: 100vh;
            div.loading-box{
                width: 50px;
                height: 50px;
                border: 3px solid white;
                border-radius: 50%;
                border-top: 3px solid transparent;
                animation: rotate 1s linear infinite;

                @keyframes rotate {
                    0%{
                        transform: rotate(0deg);
                    }
                    100%{
                        transform: rotate(360deg);
                    }
                }
            }

            span{
                color:white;
                margin-top: 20px;
                font-weight: bold;
            }
        }

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