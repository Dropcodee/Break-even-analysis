<template>
  <div class="home flex justify-evenly items-center">
    <!-- component -->
    <div class="leading-loose">
      <form class="max-w-xl m-4 p-10 bg-white rounded shadow-xl">
        <p class="text-gray-800 font-medium">Break Even Analysis</p>
        <div class="">
          <label class="block text-sm text-gray-00" for="cus_name">Firm's Name </label>
          <input class="w-full px-5 py-1 text-gray-700 bg-gray-200 rounded" v-model="firmName" required="" placeholder="Firm's Name" aria-label="Firm's Name">
        </div>
        <div class="mt-2">
          <label class="block text-sm text-gray-600" for="cus_email">Firm's Selling Price</label>
          <input class="w-full px-5  py-4 text-gray-700 bg-gray-200 rounded" v-model="sellingPrice" type="text" required="" placeholder="Firm's Selling Price" aria-label="Selling Price">
        </div>
        <div class="mt-2">
          <label class=" block text-sm text-gray-600" for="cus_email">Firm's Fixed Cost</label>
          <input class="w-full px-2 py-2 text-gray-700 bg-gray-200 rounded" v-model="fixedCost" type="text" required="" placeholder="Firm's Fixed Cost" aria-label="Fixed Cost">
        </div>
        <div class="mt-2">
          <label class=" text-sm block text-gray-600">Firm's Variable Cost</label>
          <input class="w-full px-2 py-2 text-gray-700 bg-gray-200 rounded" v-model="variableCost" type="text" required="" placeholder="Firm's Variable Cost" aria-label="Variable Cost">
        </div>
        <div class="inline-block mt-2 w-1/2 pr-1">
          <label class=" block text-sm text-gray-600" for="cus_email"> Firm's Sales Units</label>
          <input class="w-full px-2 py-2 text-gray-700 bg-gray-200 rounded" v-model="salesUnits" type="text" required="" placeholder="Enter Sales Units" aria-label="sales unit">
        </div>
        <div class="inline-block mt-2 -mx-1 pl-1 w-1/2">
          <label class="hidden block text-sm text-gray-600" for="cus_email">Percentage Increase</label>
          <input class="w-full px-2 py-2 text-gray-700 bg-gray-200 rounded" v-model="percentageIncrease" type="text" required="" placeholder="" aria-label="Email">
        </div>
        <div class="">
          <label class="block text-sm text-gray-600" for="cus_name">Percentage Decrease</label>
          <input class="w-full px-2 py-2 text-gray-700 bg-gray-200 rounded" v-model="percentageDecrease" type="text" required="" placeholder=" Percentage decrease." aria-label="Name">
        </div>
        <div class="mt-4">
          <button class="px-4 py-1 text-white font-light tracking-wider bg-gray-900 rounded" @click.prevent="clearData" type="submit">Clear Fields</button>
        </div>
      </form>
    </div>
    <div class="max-w-6xl m-4 p-10 bg-white rounded shadow-xl">
      <h2 class="text-gray-800 text-3xl font-semibold mt-2">Break Even Calculation Results</h2>
      <p class="text-gray-600 text-semibold">Fill out the form to view result</p>
      <transition name="fade">
        <div class="bg-green-600 border rounded shadow p-2 mt-4">
          <div class="flex flex-row items-center">
            <div class="flex-shrink pl-1 pr-4"><i class="fa fa-wallet fa-2x fa-fw fa-inverse"></i></div>
            <div class="flex-1 text-right">
              <h5 class="text-white">Firm's Break Even</h5>
              <h3 class="text-white text-3xl">{{ breakEven }}<span class="text-green-400"><i class="fas fa-caret-down"></i></span></h3>
            </div>
          </div>
        </div>
      </transition>
      <transition name="fade">
      <div class="bg-green-600 border rounded shadow p-2 mt-4">
        <div class="flex flex-row items-center">
          <div class="flex-shrink pl-1 pr-4"><i class="fa fa-wallet fa-2x fa-fw fa-inverse"></i></div>
          <div class="flex-1 text-right">
            <h5 class="text-white">Firm's Profit</h5>
            <h3 class="text-white text-3xl">{{ companyProfit }}<span class="text-green-400"><i class="fas fa-caret-down"></i></span></h3>
          </div>
        </div>
      </div>
    </transition>
      <transition name="fade">
      <div class="bg-green-600 border rounded shadow p-2 mt-4">
        <div class="flex flex-row items-center">
          <div class="flex-shrink pl-1 pr-4"><i class="fa fa-wallet fa-2x fa-fw fa-inverse"></i></div>
          <div class="flex-1 text-right">
            <h5 class="text-white">Profit Increase By {{ percentageIncrease }}%</h5>
            <h3 class="text-white text-3xl">{{ profitPercentageIncrease }}%<span class="text-green-400"><i class="fas fa-caret-down"></i></span></h3>
          </div>
        </div>
      </div>
    </transition>
    <transition name="fade">
      <div class="bg-green-600 border rounded shadow p-2 mt-4">
        <div class="flex flex-row items-center">
          <div class="flex-shrink pl-1 pr-4"><i class="fa fa-wallet fa-2x fa-fw fa-inverse"></i></div>
          <div class="flex-1 text-right">
            <h5 class="text-white">Profit Decrease By {{ percentageDecrease }}%</h5>
            <h3 class="text-white text-3xl">{{ profitPercentageDecrease }}%<span class="text-green-400"><i class="fas fa-caret-down"></i></span></h3>
          </div>
        </div>
      </div>
    </transition>
    </div>
  </div>
</template>
<script>
export default {
  name: 'Home',

  data () {
    return {
      firmName: null,
      sellingPrice: null,
      fixedCost: null,
      variableCost: null,
      salesUnits: null,
      companyProfit: 0,
      percentageIncrease: 0,
      percentageDecrease: 0,
      profitPercentageIncrease: 0,
      profitPercentageDecrease: 0,
      breakEven: 0
    }
  },
  methods: {
    clearData () {
      this.firmName = null
      this.sellingPrice = null
      this.fixedCost = null
      this.variableCost = null
      this.salesUnits = null
      this.companyProfit = 0
      this.percentageIncrease = 0
      this.percentageDecrease = 0
      this.profitPercentageIncrease = 0
      this.profitPercentageDecrease = 0
      this.breakEven = 0
    },
    CalculateBreakEven () {
      if (this.sellingPrice.length && this.fixedCost.length && this.variableCost.length) {
        const breakeven = this.fixedCost / (this.sellingPrice - this.variableCost)
        this.breakEven = breakeven
      }
      return 0
    },
    CalculateProfits () {
      const profits = ((this.sellingPrice - this.variableCost) * this.salesUnits) - this.fixedCost
      this.companyProfit = profits
    },
    CalculateProfitIncrease () {
      const profits = ((this.sellingPrice - this.variableCost) * this.salesUnits * (1 + (this.percentageIncrease / 100))) - this.fixedCost
      const Percentageincrease = ((profits - this.companyProfit) / this.companyProfit) * 100
      this.profitPercentageIncrease = Percentageincrease
    },
    CalculateProfitDecrease () {
      const decreaseProfit = ((this.sellingPrice - this.variableCost) * this.salesUnits * (1 - (this.percentageDecrease / 100))) - this.fixedCost
      const percentageDecrease = ((this.companyProfit - decreaseProfit) / this.companyProfit) * 100
      this.profitPercentageDecrease = percentageDecrease
    }
  },
  watch: {
    variableCost: {
      handler: function (variableCost) {
        if (variableCost.length) {
          this.CalculateBreakEven()
        }
      }
    },
    salesUnits: {
      handler: function (salesUnits) {
        if (salesUnits.length) {
          this.CalculateProfits()
        }
      }
    },
    percentageIncrease: {
      handler: function (increase) {
        if (increase.length) {
          this.CalculateProfitIncrease()
        }
      }
    },
    percentageDecrease: {
      handler: function (increase) {
        if (increase.length) {
          this.CalculateProfitDecrease()
        }
      }
    }
  }
}

</script>
<style>
.fade-enter-active,
.fade-leave-active {
  transition-property: opacity;
  transition-duration: .25s;
}

.fade-enter-active {
  transition-delay: .25s;
}

.fade-enter,
.fade-leave-active {
  opacity: 0
}

</style>
