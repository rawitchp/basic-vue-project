<template>
  <div>
    <div>
      <img :src="pic" :width="size" :height="size" />
    </div>
    <form @submit.prevent="submitForm">
      <label>
        ป้อนชื่อเล่น: 
      </label>
      <input type="text" v-on:input="setNickName"/>
      <button type="submit">Submit</button>

    </form>
    <br/>
    Hello, {{ getFullName() }}
    <div>Nickname: {{ nickName }}</div>
    <p>Age: {{ age }}</p>
    <p>address: <span v-html="address"></span></p>

    <a :href="social" target="_blank">Facebook</a>
    <p>Hobby: {{ hobby[0] }}, {{ hobby[1] }}, {{ hobby[2] }}</p>
    <p>
      <ul>
        <li>Gender: {{ general.gender }}</li>
        <li>Weight: {{ general.weight }}</li>
        <li>Height: {{ general.height }}</li>
        <li>Status: {{ general.status }}</li>
      </ul>
    </p>
    <button @click="showData">คลิกเพื่อดูข้อมูล</button>
    <button @click="increment(10)">Increase</button>
    <button @click="decrement(5)">Decrease</button>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      firstName: 'Rawitch',
      lastName: 'Payakkawan',
      nickName:"",
      age: 21,
      address: '<strong>BKK</strong>',
      pic: 'https://scontent.fbkk28-1.fna.fbcdn.net/v/t1.6435-9/128806075_3531416196942199_3675393776492421544_n.jpg?_nc_cat=106&ccb=1-7&_nc_sid=09cbfe&_nc_ohc=UlrpLoCm09kAX9jykOM&_nc_pt=1&_nc_ht=scontent.fbkk28-1.fna&oh=00_AfCK3Yq3j2pwahZHrwQaffbvlLYG3pl7jPIF_k9FxGUYIQ&oe=6480121C',
      size: 150,
      social: 'https://www.facebook.com/rawitch.payakkawan',
      hobby: ['game', 'music', 'sport'],
      general: {
        gender: 'male',
        weight: 70,
        height: 178,
        status: false,
      },
    };
  },
  methods: {
    getFullName() {
      return `${this.firstName} ${this.lastName}`;
    },
    showData(){
      alert(this.firstName)
    },
    increment(val){
      this.age+=val
    },
    decrement(val){
      this.age-=val
    },
    setNickName(e){
      this.nickName = e.target.value
      console.log(e.target.value)
    },
    submitForm(e){
     
      alert('บันทึกเรียบร้อย')
    }
  },
};
</script>

<style></style>
