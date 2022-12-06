<template>
  <div class="advice-box">
    <div class="text">
      <h5 class="title">Advice {{ slips.id }}</h5>
      <p>{{ slips.advice }}</p>
      <img
        class="divider"
        src="./../assets/pattern-divider-desktop.svg"
        alt="divider"
      />
    </div>
    <button @click="getPost" class="btn-dice">
      <img class="dice" src="./../assets/icon-dice.svg" alt="dice" />
    </button>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "AdviceBox",
  id: null,
  advice: null,
  props: {
    msg: String,
  },
  data() {
    return {
      slips: {
        id: '',
        advice: ''
      },
    };
  },

  methods: {
    getPost() {
      axios
        .get("https://api.adviceslip.com/advice")
        .then((response) => {
          console.log(response.data);
          this.$data.slips.id = response.data.slip.id;
          this.$data.slips.advice = response.data.slip.advice;
        })
        .catch((error) => {
          console.log(error);
        });
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.advice-box {
  background: #313a49;
  color: #fff;
  display: flex;
  width: 550px;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  text-align: center;
  border-radius: 10px;
  position: relative;
}

.text {
  padding: 30px 30px;
}

.title {
  color: #4bd595;
}

.divider {
  padding: 10px 0;
}

@keyframes glowing {
  0% {
    background-color: #2ba805;
    box-shadow: 0 0 5px #2ba805;
  }
  50% {
    background-color: #49e819;
    box-shadow: 0 0 20px #49e819;
  }
  100% {
    background-color: #2ba805;
    box-shadow: 0 0 5px #2ba805;
  }
}
.btn-dice {
  width: 50px;
  height: 50px;
  display: flex;
  justify-content: center;
  align-items: center;
  border-radius: 50%;
  background: #53ffab;
  border: none;
  cursor: pointer;
  bottom: -25px;
  position: absolute;
  box-shadow: 0 0 5px #2ba805;
  animation: glowing 1300ms infinite;
}
.dice {
  padding: 4px;
  width: 30px;
}
</style>
