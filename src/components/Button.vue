<template>
      <button @click="acceptOrder">
          <span>Order now</span>
          <div class="btn-order">
              <span id="total">{{totalSum}} $</span>
          </div>
      </button>

</template>

<script>
import {mapGetters} from 'vuex'
import {mutationTypes as deliveryMutationTypes} from '@/store/modules/delivery'


export default {
    name: 'FkButton',
    props: {
        payload: {
            type: Object
        },
        totalSum: {
            type: Number,
            required: true
        }
    },
    methods: {
        acceptOrder() {
            this.$store.commit(deliveryMutationTypes.addDeliveryInfo, this.payload);
            this.$router.push({name: 'orderInfo'})
        }
    },
    computed: {
        ...mapGetters([
            'productSumValue'
        ])
    }
}
</script>

<style scoped>
button {
    display: inline-block;
    width: 355px;
    height: 58px;
    border-radius: 5px;
    background: linear-gradient(#99E061, #7AC93B);
    margin-top: 40px;
    margin-left: 30px;
    margin-right: 0;
    padding: 0;
    font-size: 10px;
    font-family: 'Inter', sans-serif;
    cursor: pointer;
}

span {
    display: inline-block;
    color: #FFFFFF;
    margin-top: 10px;
    margin-right: 0;
}

.btn-order {
    display: inline-block;
    position: relative;
    top: -2px;
    left: 90px;
    text-align: center;
    width: 59px;
    height: 38px;
    border-radius: 5px;
    background-color: #FFFFFF;
    font-size: 10px;
    
}

#total {
    display: block;
    color: black;
    margin-top: 7px;
    font-size: 18px;
}
</style>