<template>
    <div id="app">
        <div id="content">
            <h1>Market Cards</h1>
            <div class="board">
                <Card
                    v-for="item in items.types"
                    :item="item"
                    :key="item.type_id">
                </Card>
            </div>
        </div>
    </div>
</template>

<script>
    import axios from 'axios';

    import Card from './components/Card.vue'

    export default {
        name: 'app',
        data: function () {
            return {
                items: []
            }
        },
        created: function () {
            axios.get('/apiExample.json')
                .then(response => {
                    // JSON responses are automatically parsed.
                    this.items = response.data
                })
                .catch(e => {
                    alert('Error, please try again later');
                    console.error(e);
                })
        },
        components: {
            Card
        }
    }
</script>

<style lang="scss">
    $defaultFontFamily: 'Roboto', Arial, Helvetica, sans-serif;
    $defaultFontSize: 16px;

    body {
        margin: 0;
        font-family: $defaultFontFamily;
        font-size: $defaultFontSize;
        background-color: #f4f3ef;
        padding: 1rem;
    }

    .board {
        display: grid;
        grid-template-columns: repeat(auto-fill, 295px);
        grid-gap: 15px;
    }
</style>
