<template>

    <div class="app" id="app">
        <div class="message">Swipe left/right to navigate</div>
        <Wine v-bind:item="item" />
    </div>

</template>

<script>

    import winesList from "./mocks/data";
    import Wine from "./components/Wine.vue";

    export default {
        name: "App",
        components: {
            Wine
        },
        data: function() {
            return {
                initTouch: 0,
                endTouch: 0,
                itemIndex: 0,
                itemsList: winesList,
                item: null
            };
        },
        created: function() {
            this.item = this.itemsList[0];
            // This value is to avoid accidental swipes
            this.swipeOffset = 150;

            document.addEventListener("touchstart", function(e) {
                this.initTouch = e.changedTouches[0].screenX;
            }.bind(this));

            document.addEventListener("touchend", function(e) {
                this.endTouch = e.changedTouches[0].screenX;

                if (this.initTouch < this.endTouch && this.endTouch - this.initTouch > this.swipeOffset) {
                    // swipe right - load prev item
                    if (this.itemsList[this.itemIndex - 1] !== undefined) {
                        this.item = this.itemsList[this.itemIndex - 1];
                        this.itemIndex--;
                    }
                } else if (this.initTouch > this.endTouch && this.initTouch - this.endTouch > this.swipeOffset) {
                    // swipe left - load next item
                    if (this.itemsList[this.itemIndex + 1] !== undefined) {
                        this.item = this.itemsList[this.itemIndex + 1];
                        this.itemIndex++;
                    }
                }
            }.bind(this));
        }
    };

</script>

<style>

    * {
        box-sizing: border-box;
        font-family: "Noto Sans JP", sans-serif;
        margin: 0;
        padding: 0;
    }

    body {
        background: rgba(50, 10, 50, 1);
    }

    .app {
        align-items: stretch;
        background: rgba(50, 10, 50, 1);
        background: linear-gradient(
            180deg,
            rgba(50, 0, 50, 1) 10%,
            rgba(85, 0, 50, 1) 60%,
            rgba(50, 10, 50, 1) 60%
        );
        display: flex;
        flex-direction: column;
        padding: 20px;
    }

    .message {
        color: #ffffff;
        display: flex;
        font-family: "Noto Sans JP", sans-serif;
        font-size: 16px;
        justify-content: center;
        margin-bottom: 20px;
    }

</style>
