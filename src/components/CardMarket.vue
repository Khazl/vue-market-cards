<template>
    <div class="card__market">
        <div class="card__market-name">
            {{ market.market_name }}
        </div>
        <div class="card__market-details">
            <table>
                <tr>
                    <td>Stock</td>
                    <td>
                        {{ market.volume_remain | number }}
                        <span v-if="market.orders">({{ market.orders.length}})</span>
                    </td>
                </tr>
                <tr>
                    <td>Max. Price</td>
                    <td>{{ market.price_highest | number }}</td>
                </tr>
                <tr>
                    <td>Min. Price</td>
                    <td>{{ market.price_lowest | number }}</td>
                </tr>
            </table>
        </div>
    </div>
</template>

<script>
    export default {
        props: {
            market: Object
        },
        filters: {
            number: function (value) {
                if (!value) return 'N/A';
                return value.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ".");
            }
        }
    }
</script>