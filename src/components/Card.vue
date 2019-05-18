<template>
    <div class="card">
        <div class="card__header">
            <div class="card__icon">
                <img :src="'https://image.eveonline.com/Type/' + item.type_id + '_32.png'"/>
            </div>
            <div class="card__title">
                {{ item.type_name }}
            </div>
        </div>
        <div class="card__content">
            <div class="card__markets">
                <div class="card__markets">
                    <CardMarket
                        v-for="market in item.markets"
                        :market="market"
                        :key="market.market_id+item.type_id">
                    </CardMarket>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    import CardMarket from './CardMarket.vue'

    export default {
        props: {
            item: Object
        },
        components: {
            CardMarket
        }
    }
</script>

<style lang="scss">
    .card {
        border-radius: 5px;
        box-shadow: 0 2px 2px rgba(204, 197, 185, 0.5);
        background-color: #fff;
        color: #252422;
        position: relative;
        overflow: hidden;
        flex-grow: 1;
        width: 100%;
        transition: box-shadow .5s;

        &:hover {
            box-shadow: 0 4px 7px rgba(204, 197, 185, 0.5);
        }

        &__header {
            border-bottom: 1px solid #F1EAE0;
            display: flex;
            align-items: center;
            padding: 10px;
            font-size: 16px;
        }

        &__icon {
            margin-right: 15px;

            img {
                display: block;
            }
        }

        &__title {
            font-weight: 600;
        }

        &__content {
            padding: 15px 15px 10px;
        }

        &__markets {
            font-size: 14px;
        }

        &__market {
            margin-bottom: 25px;

            &:last-of-type {
                margin-bottom: 0;
            }
        }

        &__market-name {
            overflow: hidden;
            text-overflow: ellipsis;
            white-space: nowrap;
            font-weight: 600;
            margin-bottom: 5px;
        }

        &__market-details {

            table {
                width: 100%;
                border-collapse: collapse;

                tr {

                    &:last-of-type {

                        td {
                            border-bottom: 0;
                        }
                    }
                }

                td {
                    border-spacing: 0;
                    border-bottom: 1px solid #F1EAE0;
                    padding: 7px 0 2px;

                    &:last-of-type {
                        text-align: right;
                        font-family: monospace;
                    }
                }
            }
        }
    }
</style>