<template>
    <div class="my_container">

        <div class="container">
            <ul>
                <li class="col-6 col-md-4 col-lg-2" v-for="(element, i) in listDisc" :key="`element-${i}`">

                    <img :src="element.poster" :alt="element.title">
                    <h3>{{ element.title }}</h3>
                    <span class="author">{{ element.author }}</span>
                    <span class="date">{{ element.year }}</span>
                    <span class="style">{{ element.genre }}</span>

                </li>
            </ul>
        </div>
    </div>
</template>

<script>
import axios from 'axios';

export default {
    name : 'Main',
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
                list-style: none;

                li{
                    padding: 10px;
                    background-color: #2e3a46;
                    margin-bottom: 20px;
                }
            }
        }
    }
</style>