<template>

    <div class="wine">
        <div class="image">
            <img class="image-img" :src="getImgUrl()" />
            <!--img class="image-img" src="./assets/bottle.png" alt="" /-->
        </div>
        <div class="detail">
            <div class="detail-title">
                {{ item.name }}
                <span class="detail-subtitle">
                {{ item.varietal }}
                </span>
            </div>

            <div class="detail-content">
                <div>{{ item.description }}</div>
                <div><span class="detail-content-key">Brand:</span> {{ item.brand }}</div>
                <div><span class="detail-content-key">Maker:</span> {{ item.maker }}</div>
                <div><span class="detail-content-key">Name:</span> {{ item.name }}</div>
                <div><span class="detail-content-key">Varietal:</span> {{ item.varietal }}</div>
                <div><span class="detail-content-key">Presetation:</span> {{ item.presentation }}</div>
                <div><span class="detail-content-key">Year:</span> {{ item.year }}</div>
                <div><span class="detail-content-key">Alcohol:</span> {{ item.alcohol }}</div>
                <div><span class="detail-content-key">Country:</span> {{ item.country }}</div>
            </div>
        </div>
    </div>

</template>

<script>

    export default {
        name: 'Wine',
        props: {
            item: Object
        },
        methods: {
            getImgUrl: function () {
            return './assets/' + this.item.img;
            }
        }
    }
</script>

<style>

    .image {
        align-items: center;
        display: flex;
        justify-content: center;
        height: 400px;
        width: 100%;
    }

    .image-img {
        height: 400px;
    }

    .detail {
        background-color: rgb(255, 255, 255);
        border-radius: 15px;
        padding: 20px;
        width: 100%;
    }

    .detail-title {
        display: flex;
        flex-direction: column;
        font-family: 'Lora', serif;
        font-size: 28px;
        margin-bottom: 30px;
    }

    .detail-subtitle {
        color: rgba(120,23,80,1);
        font-family: 'Oswald', sans-serif;
        font-size: 14px;
    }

    .detail-content {
        display: flex;
        flex-direction: column;
        font-size: 16px;
        line-height: 30px;
    }

    .detail-content > div:first-child {
        line-height: 20px;
        margin-bottom: 20px;
    }

    .detail-content-key {
        font-family: 'Oswald', sans-serif;
        letter-spacing: .5px;
    }

</style>