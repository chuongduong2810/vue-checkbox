<template>
  <div class="hello">
    <ul>
      <li v-for="item in listReason" :key="item.id">
        <div class="item">
            <input type="checkbox" v-model="item.active">
            {{ item.text }}
        </div>
      </li>
      <textarea v-model="textArea"></textarea>
    </ul>
    <button class="submit" @click="handleSubmit()">Gửi thông tin</button>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {
    msg: String,
  },
  data() {
    return {
      listReason: [
        {
          id: 1,
          text: "Khong muon mua nua",
          active: true,
        },
        {
          id: 2,
          text: "Doi dia chi",
          active: false,
        },
        {
          id: 3,
          text: "Tim thay gia re hon",
          active: false,
        },
      ],
      textArea: ''
    };
  },
  methods: {
    handleSubmit(){
      let reasonIsTrue = this.listReason.filter(item=>item.active === true)
      let temp = ''
      reasonIsTrue.forEach(item => {
        if (temp != '')
        temp = `${temp} - ${item.text}`
        else temp = item.text
      })
      console.log(temp,this.textArea);
    }
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
