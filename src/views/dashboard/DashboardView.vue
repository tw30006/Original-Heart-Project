<template>
    <h2>這是後台</h2>
    <nav class="navbar navbar-expand-lg bg-body-tertiary">
      <div class="container-fluid">
          <a class="navbar-brand" href="#">Navbar</a>
          <button class="navbar-toggler" type="button"
          data-bs-toggle="collapse" data-bs-target="#navbarNav"
          aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
          <span class="navbar-toggler-icon"></span>
          </button>
          <div class="collapse navbar-collapse" id="navbarNav">
          <ul class="navbar-nav">
              <li class="nav-item">
              <RouterLink class="nav-link active" to="/admin/products">產品列表</RouterLink>
              </li>
              <li class="nav-item">
              <RouterLink class="nav-link active" to="/admin/order">購物車訂單</RouterLink>
              </li>
              <li class="nav-item">
              <RouterLink class="nav-link active" to="/">前台</RouterLink>
              </li>
          </ul>
          </div>
      </div>
    </nav>
    <RouterView></RouterView>
</template>

<script>
import axios from 'axios';
import Swal from 'sweetalert2';

const { VITE_APP_API_URL } = import.meta.env;

export default {
  methods: {
    checkLogin() {
      const url = `${VITE_APP_API_URL}/api/user/check`;
      axios.post(url)
        .then(() => {
          Swal.fire('驗證成功！');
        })
        .catch(() => {
          this.$router.push('/login');
        });
    },
  },
  mounted() {
    const token = document.cookie.replace(
      /(?:(?:^|.*;\s*)hexToken\s*=\s*([^;]*).*$)|^.*$/,
      '$1',
    );
    axios.defaults.headers.common.Authorization = token;
    this.checkLogin();
  },
};
</script>
