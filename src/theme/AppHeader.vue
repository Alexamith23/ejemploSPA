<template>
  <nav class="nav has-shadow">
    <div class="container">
      <router-link to="/" exact>
        <img src="https://coding-rs.s3.amazonaws.com/images/spa-vue/logo.png" alt="Vue SPA" />
      </router-link>

      <router-link class="nav-item is-tab" to="/">
          Guia Hoteles
      </router-link>

      <router-link class="nav-item is-tab"
        :to="{ name: 'category', params: { id: 'mobile' } }">Hoteles
      </router-link>

    </div>
  </nav>
</template>
