<template>
  <div>
    <div class="number" :id="'number-'+number" v-for="number in listOfRandomNumbers()" :key="number" @mouseover="highlight(number)" @mouseout="reset" ref="numberRef">
      {{number}}
    </div>
  </div>
</template>

<script>
export default {
  
  data()
  {
    return {
      limit: this.$parent.limit,
      numbers: []
    }
  },
  watch: {
    ['$parent.limit'](newLimit)
    {
      this.limit = newLimit;
    }
  },
  methods: {
    listOfRandomNumbers()
    {
      let numbers = [];
      for(var i = 0; i < this.limit; i++)
      {
        numbers = [...numbers, i];
      }
      return numbers.sort(() => Math.random() - 0.5);
    },
    highlight(number)
    {
      const nums = document.querySelectorAll('.number');

      for(let i = 0; i < nums.length; i++)
      {
        const num = nums[i].textContent.trim();
        if(number % num === 0)
        {
          nums[i].classList.add('active')
          console.log('divisor', num)
        }
      }
    },
    reset()
    {
      const nums = document.querySelectorAll('.number');
      nums.forEach(num => num.classList.remove('active'))
    }
  }
}
</script>

<style scoped>
	.number {
		display: inline-block;
		padding: 5px;
		background-color: lightgrey;
		margin: 5px;
	}

	.active {
		background-color: red;
	}
</style>
