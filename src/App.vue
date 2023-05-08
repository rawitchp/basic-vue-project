<template>
  <img :src="pic" :width="size" :height="size" ref="imageEl" />
  <br />
  Hello, {{ getFullName }}
  <p>Age: {{ age }} ปี</p>
  <p>Salary: {{ salary }} บาท</p>
  <p>รายได้ต่อปี: {{ getIncome }} บาท</p>
  <p>ตำแหน่งงาน: {{ getDepartment }}</p>
  <button @click="incrementSalary(5000)">เพิ่มเงินเดือน</button>
  <button @click="decrementSalary(5000)">ลดเงินเดือน</button>
  <button @click="toggleVisible">
    {{ isVisible ? 'ซ่อน' : 'แสดง' }}รายละเอียด
  </button>
  <article v-show="isVisible">
    <p>address: <span v-html="address"></span></p>
    <a :href="social" target="_blank">Facebook</a>
    <p v-if="hobby.length === 0">ไม่มีงานอดิเรก</p>
    <div v-else>
      <p>งานอดิเรก :</p>
      <ul>
        <li v-for="(item, i) in hobby" :key="i">{{ item }}</li>
      </ul>
    </div>
    <div>
      <p>ข้อมูลพื้นฐาน :</p>
      <ul>
        <li v-for="(item, key) in general" :key="key">
          {{ key }} - {{ item }}
        </li>
      </ul>
    </div>
  </article>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      firstName: 'Rawitch',
      lastName: 'Payakkawan',
      age: 21,
      address: '<i>BKK</i>',
      pic: 'https://scontent.fbkk28-1.fna.fbcdn.net/v/t1.6435-9/128806075_3531416196942199_3675393776492421544_n.jpg?_nc_cat=106&ccb=1-7&_nc_sid=09cbfe&_nc_ohc=UlrpLoCm09kAX9jykOM&_nc_pt=1&_nc_ht=scontent.fbkk28-1.fna&oh=00_AfCK3Yq3j2pwahZHrwQaffbvlLYG3pl7jPIF_k9FxGUYIQ&oe=6480121C',
      size: 150,
      social: 'https://www.facebook.com/rawitch.payakkawan',
      hobby: ['game', 'music', 'sport', 'internet'],
      general: {
        gender: 'male',
        weight: 70,
        height: 178,
        status: false,
      },
      isVisible: false,
      salary: 20000,
    };
  },
  methods: {
    toggleVisible() {
      this.isVisible = !this.isVisible;
    },
    incrementSalary(val) {
      this.salary += val;
    },
    decrementSalary(val) {
      this.salary -= val;
    },
  },
  computed: {
    getFullName() {
      return `${this.firstName} ${this.lastName}`;
    },
    getIncome() {
      return this.salary * 12;
    },
    getDepartment() {
      return this.salary >= 35000 ? 'Project Managaer' : 'Programmer';
    },
  },
  watch: {
    salary(val) {
      if (val > 50000) {
        alert('เงินเดือนไม่ควรเกิน 50000 บาท');
        setTimeout(() => {
          this.salary = 50000;
        }, 100);
      }
    },
  },
};
</script>

<style></style>
