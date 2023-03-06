<script>
import axios from "axios";

export default {
    data() {
        return {
            cards: []
        }
    },

    // components: {
    //   MyComponent,
    // },

    created() {
        axios
            .get("https://db.ygoprodeck.com/api/v7/cardinfo.php?num=10&offset=0")
            .then((response) => {
                console.log(response)
                this.cards = response.data.data;
            })
    }
};
</script>

<template>
    <div class="container content">
        <div class="row">
            <div class="col" v-for="card in cards">
                <img :src="card.card_images[0].image_url" class="img-fluid" alt="">
                <h1>{{ card.name }}</h1>
            </div>
        </div>
    </div>
</template>

<style lang="scss" scoped>
.content {
    background-color: white;
}
</style>