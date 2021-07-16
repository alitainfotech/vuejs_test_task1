<template>
  <div>
    <Navbar/>
    <section class="cards-sec">
      <div class="container">
        <div class="row row-one">

          <div class="col-md-3">
            <div class="card-box">
              <h2>NEW ORDERS</h2>

              <div v-for="(order,index) in new_orders" :key="index">
                <CardOrder :order="order"/>
              </div>

            </div>
          </div>

          <div class="col-md-3">
            <div class="card-box">
              <h2>IN PROGRESS</h2>

              <div v-for="(order,index) in orders_in_progress" :key="index">
                <CardOrder :order="order"/>
              </div>

            </div>
          </div>

          <div class="col-md-3">
            <div class="card-box">
              <h2>WAITING FOR BUYER</h2>

              <div v-for="(order,index) in orders_in_waiting" :key="index">
                <CardOrder :order="order"/>
              </div>

            </div>
          </div>

          <div class="col-md-3">
            <div class="card-box">
              <h2>COMPLETED</h2>

              <div v-for="(order,index) in orders_complete_and_cancel" :key="index">
                <CardOrder :order="order"/>
              </div>

            </div>
          </div>

        </div>
      </div>
    </section>
  </div>
</template>
<script lang="ts">
  import { Component, Vue } from 'vue-property-decorator';
  import Navbar from '@/components/Navbar';
  import CardOrder from '@/components/CardOrder';

  @Component({
    components: {
      Navbar,
      CardOrder
    },
    computed: {
      new_orders() {
        return this.orders.filter(order => {
          if(order.status == 0){
            return order;
          }
        });
      },
      orders_in_progress() {
        return this.orders.filter(order => {
          if(order.status == 1){
            return order;
          }
        });
      },
      orders_in_waiting() {
        return this.orders.filter(order => {
          if(order.status == 2){
            return order;
          }
        });
      },
      orders_complete_and_cancel() {
        return this.orders.filter(order => {
          if(order.status == 3 || order.status == 4){
            return order;
          }
        });
      }
    },
    methods:{
      deleteOrder(orderId){
        const i = this.orders.map(order => order.id).indexOf(orderId);
        this.orders.splice(i, 1);
      }
    }
  })
  export default class Home extends Vue {
    orders = [
      {
        id:1,
        days:5,
        hours:20,
        price:320,
        status:0
      },
      {
        id:2,
        days:3,
        hours:4,
        price:85,
        status:0
      },
      {
        id:3,
        days:5,
        hours:5,
        price:155,
        status:1
      },
      {
        id:4,
        days:3,
        hours:8,
        price:385,
        status:1
      },
      {
        id:5,
        days:5,
        hours:3,
        price:385,
        status:2
      },
      {
        id:6,
        days:5,
        hours:20,
        price:346,
        status:3,
        date:'Dec 13, 9:43PM'
      },
      {
        id:7,
        days:5,
        hours:20,
        price:320,
        status:3,
        date:'Dec 12, 8:21PM'
      },
      {
        id:8,
        days:5,
        hours:20,
        price:385,
        status:4,
        date:'Dec 13, 9:43PM'
      }
    ]
  }
</script>