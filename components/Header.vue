<template>
  <header>
    <b-navbar toggleable="lg" type="light" variant="light">
        <b-navbar-brand href="/">nuxt開発実験室</b-navbar-brand>

        <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

        <b-collapse id="nav-collapse" is-nav>
          <b-navbar-nav>
            <NuxtLink to="/todo">TODOリスト</NuxtLink>
          </b-navbar-nav>
        </b-collapse>
    </b-navbar>
  </header>
</template>

<style>
</style>