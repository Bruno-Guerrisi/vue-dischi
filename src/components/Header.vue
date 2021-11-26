<template>
  <div class="my_container p-2">
        <img class="h-100" src="../assets/logo.png" alt="">

        <div>
            <select v-model.trim="genres" @change="$emit('selectSearch', genres)">
                <option value="all">All</option>
                <option value="rock">Rock</option>
                <option value="pop">Pop</option>
                <option value="jazz">Jazz</option>
                <option value="metal">Metal</option>
            </select>
        </div>
  </div>
</template>

<script>
export default {
    name : 'Header',
    data() {
        return {
            genres: '',
        };
    },
}
</script>

<style lang="scss" scoped>

    div.my_container{
        height: 60px;
        background-color: #2e3a46;
        display: flex;
        justify-content: space-between;
        align-items:center;

        div{
            select{
                width: 150px;
                border: 2px solid #17232e;
                background-color: #1d2d3c;
                border-radius: 5px;
                color: white;
            }
        }
    }
</style>