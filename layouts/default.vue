<template>
  <div>
    <div>
      <b-navbar class="is-dark">
        <template #brand>
          <b-navbar-item tag="router-link" :to="{ path: '/' }">
            <img
              src="https://raw.githubusercontent.com/buefy/buefy/dev/static/img/buefy-logo.png"
              alt="Lightweight UI components for Vue.js based on Bulma"
            />
          </b-navbar-item>
        </template>
        <template #start>
          <b-navbar-item href="/"> Post </b-navbar-item>
          <b-navbar-dropdown label="Admin">
            <b-navbar-item href="/postlist"> Post list </b-navbar-item>
          </b-navbar-dropdown>
        </template>
      </b-navbar>
    </div>
    <nuxt />
  </div>
</template>