<template>
    <h2>登入頁面</h2>
    <div class="container">
        <div class="row justify-content-center">
          <h1 class="h3 mb-3 font-weight-normal">
            請先登入
          </h1>
          <div class="col-3 col-md-4 col-xl-6">
            <form id="form" class="form-signin" @submit.prevent="login">
              <div class="form-floating mb-3">
                <input type="email" class="form-control" v-model="user.username"
                id="floatingUsername" placeholder="name@example.com" required autofocus>
                <label for="username">Email address</label>
                </div>
                <div class="form-floating">
                <input type="password" class="form-control" v-model="user.password"
                id="floatinPassword" placeholder="Password" required>
                <label for="password">Password</label>
                </div>
              <button class="btn btn-lg btn-primary w-100 mt-3" type="submit">
                登入
              </button>
            </form>
          </div>
        </div>
        <p class="mt-5 mb-3 text-muted">
          &copy; 2021~∞ - 六角學院
        </p>
    </div>
</template>

<script>
import axios from 'axios';

const { VITE_APP_API_URL } = import.meta.env;

export default {
  data() {
    return ({
      user: {
        username: '',
        password: '',
      },
    });
  },
  methods: {
    login() {
      const apiUrl = `${VITE_APP_API_URL}/admin/signin`;
      //   const path = 'sponge';
      axios.post(`${apiUrl}`, this.user)
        .then((res) => {
          const { token, expired } = res.data;
          document.cookie = `hexToken=${token}; expires=${new Date(expired)};`;
          this.$router.push('/admin/products');
        })
        .catch(() => {
        //   Swal.fire("登入失敗，請重新輸入！");
        });
    },
  },
};
</script>
