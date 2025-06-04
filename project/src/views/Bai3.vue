<template>
 <div class="container mt-5 ">
  <div class="row shadow p-3 mb-5 bg-body rounded g-3">
    <div class="col-4  p-3">
      <h3 class="text-primary">Form Đăng ký</h3>
      <div class="form">
        <form @submit.prevent="register">
          <div class="mb-3">
            <label for="Text">Họ Tên:</label>
            <input type="text" id="Text" class="form-control" v-model="name" required />
          </div>
          <div class="mb-3">
            <label for="email">Email:</label>
            <input type="email" id="email" class="form-control" v-model="email" required />
          </div>
          <div class="mb-3">
            <label for="password">Mật khẩu:</label>
            <input type="password" id="password" class="form-control" v-model="password" required />
          </div>
           <div class="mb-3">
            <label for="dob">Ngày sinh:</label>
            <input type="date" id="dob" class="form-control" v-model="dob" required />
          </div>
           <div class="mb-3 d-inline-flex">
            <label for="radio" class="me-2">Giới tính:</label>
            <div>
              <input type="radio" id="male" value="nam" v-model="gender" required />
              <label for="male">Nam</label>
            </div>
            <div>
              <input type="radio" id="female" value="nữ" v-model="gender" required />
              <label for="female">Nữ</label>
            </div>
              <div>
              <input type="radio" id="other" value="khác" v-model="gender" required />
              <label for="other">Khác</label>
            </div>
          </div>
           <div class="mb-3 d-inline-flex"> 
            <label for="checkbox" class="me-2">Ngôn ngữ:</label>
            <div>
              <input type="checkbox" id="vn" value="vn" v-model="language" />
              <label for="vn">Tiếng Việt</label>
            </div>
            <div>
              <input type="checkbox" id="en" value="en" v-model="language" />
              <label for="en">Tiếng Anh</label>
            </div>
              <div>
              <input type="checkbox" id="other" value="other" v-model="language" />
              <label for="other">Tiếng Nhật</label>
            </div>
          </div>
          <button type="submit" class="btn btn-primary">Đăng ký</button>
        </form>
      </div>
    </div>
    <div class="col-6 p-3 mx-auto ">
      <h3 class="text-primary">Thông tin đã đăng ký</h3>
      <div class="p-3 text-start"style="border: 1px solid #ccc; border-radius: 5px;">
        <p><strong>Họ Tên:</strong> {{ name }}</p>
        <p><strong>Email:</strong> {{ email }}</p>
        <p><strong>Ngày sinh:</strong> {{ dob }}</p>
        <p class="text-start"><strong>Giới tính:</strong> {{ gender }}</p>
        <p><strong>Ngôn ngữ:</strong> {{ language.join(', ') }}</p>
    </div>
  </div>
  </div>
</div>
</template>

<script setup>
import { ref } from 'vue';

const name = ref('');
const email = ref('');
const dob = ref('');
const date= ref('');
const gender = ref('');
const language = ref([]);
const register = () => {
  const userInfo = {
    name: name.value,
    email: email.value,
    dob: dob.value,
    date: date.value,
    gender: gender.value,
    language: language.value
  };
  console.log('User Information:', userInfo);
};
</script>
<style scoped>
input[type="radio"],
input[type="checkbox"] {
  margin-right: 5px;
}
input[type="radio"] + label,
input[type="checkbox"] + label {
  margin-right: 10px;
}
input[type="radio"]:checked + label,
input[type="checkbox"]:checked + label {
  font-weight: bold;
}
</style>