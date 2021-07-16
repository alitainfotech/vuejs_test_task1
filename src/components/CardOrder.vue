<template>
    <div class="card-inner" >
        <div class="card-menu">
            <a href="#" @click="deleteOrder(order.id)"><b-icon icon="three-dots" scale="1.3" variant="secondary" ></b-icon></a>
        </div>
        <div class="card-detail">
            <div class="img-product">
                <img src="../assets/images/img1.png">
            </div>

            <div class="card-content" v-if="order.status == 0">
                <span class="del-status">New order</span>
                <p class="p-days"><b-icon icon="clock" scale="0.9" variant="secondary" ></b-icon>{{ order.days }} Days Left</p>
                <p class="p-price"><span class="span-hrs">{{ order.hours }} hrs</span> <span class="price-one">${{ order.price }}</span></p>
            </div>
            <div class="card-content" v-else-if="order.status == 1">
                <span class="del-status del-status-in-progress">in progress</span>
                <p class="p-days"><b-icon icon="clock" scale="0.9" variant="secondary" ></b-icon>Due in {{ order.days }} Days </p>
                <p class="p-price"><span class="span-hrs">{{ order.hours }} hrs</span> <span class="price-one">${{ order.price }}</span></p>
            </div>
            <div class="card-content" v-else-if="order.status == 2">
                <span class="del-status del-status-waiting">delivered</span>
                <p class="p-days"><b-icon icon="clock" scale="0.9" variant="secondary" ></b-icon> {{ order.days }} Days Left</p>
                <p class="p-price"><span class="span-hrs">{{ order.hours }} hrs</span> <span class="price-one">${{ order.price }}</span></p>
            </div>
            <div class="card-content" v-else-if="order.status == 3">
                <span class="del-status del-status-completed">completed</span>
                <p class="p-days"><b-icon icon="clock" scale="0.9" variant="secondary" ></b-icon> {{ order.date }}</p>
                <p class="p-price"><span class="price-one">${{ order.price }}</span></p>
            </div>
            <div class="card-content" v-else-if="order.status == 4">
                <span class="del-status del-status-canceled">canceled</span>
                <p class="p-days"><b-icon icon="clock" scale="0.9" variant="secondary" ></b-icon> {{ order.date }}</p>
                <p class="p-price"><span class="span-hrs">{{ order.hours }} hrs</span><span class="price-one">${{ order.price }}</span></p>
            </div>
        </div>
        <div class="order-detail">
            <a href="#" class="view-a">View Order</a>
            <ul class="order-one">
                <li class="chat-li"><a href="#"><b-icon icon="chat" scale="0.8" variant="secondary" ></b-icon></a></li>
                <li class="profile-li"><a href="#"><img src="../assets/images/ppl-1.jpg" /></a></li>
            </ul>
        </div>
    </div>
</template>
<script lang="ts">
    import { Component, Vue } from 'vue-property-decorator';

    @Component({
        components: {
        },
        props: ['order'],
        methods:{
            deleteOrder(orderId){
                this.$parent.deleteOrder(orderId);
            }
        }
    })
    export default class CardOrder extends Vue {}
</script>