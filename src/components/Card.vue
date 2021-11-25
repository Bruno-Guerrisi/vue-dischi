<template>

    <div class="main-container">
        <div class="image-container">
            <img :src="url" :alt="title">
        </div>

        <h3>{{ title }}</h3>
        <span class="author">{{ author }}</span>
        <span class="date">{{ date }}</span>
        <span class="style">{{ genre }}</span>
    </div>
</template>

<script>
export default {
name: 'Card',
props: {
    url: String,
    title: String,
    author: String,
    date: String,
    genre: String,
}
}
</script>

<style lang="scss" scoped>

    div.main-container{
        padding: 10px;
    }
    div{
        background-color: #2e3a46;
        height: 100%;
        display: flex;
        flex-direction: column;
        align-items: center;
        text-align: center;

        .image-container{
            height: 150px;
        }

        h3{
            color:white;
            font-size: 18px;
            text-align: center;
        }

        .author{
            font-size: 16px;
        }
        
        .date{
            font-size: 14px;
        }
        .author,
        .date{
            color: #7a7a7a;
        }

        .style{
            color: white;
            font-size: 16px;
            font-weight: bold;
        }
    }

</style>