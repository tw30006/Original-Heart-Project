import { RouterLink } from 'vue-router';

import { RouterLink } from 'vue-router';
import { RouterLink } from 'vue-router';
<template>
    <h2>這是前台</h2>
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
                    <RouterLink class="nav-link active" to="/">首頁</RouterLink>
                    </li>
                    <li class="nav-item">
                    <RouterLink class="nav-link active" to="/about">品牌故事</RouterLink>
                    </li>
                    <li class="nav-item">
                    <RouterLink class="nav-link active" to="/products">商品</RouterLink>
                    </li>
                    <li class="nav-item">
                    <RouterLink class="nav-link active" to="/login">登入</RouterLink>
                    </li>
                    <li class="nav-item">
                    <RouterLink class="nav-link active" to="/cart">購物車</RouterLink>
                    </li>
                    <li class="nav-item">
                    <RouterLink class="nav-link active" to="/admin/products">後台 購物車列表</RouterLink>
                    </li>
                </ul>
                </div>
            </div>
        </nav>
    <RouterView></RouterView>
</template>
