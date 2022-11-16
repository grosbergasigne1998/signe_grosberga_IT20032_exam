<script>
export default {
  name: "NavigationComponent",
  data() {
    return {
      addresses: [{ path: "/", name: "SONGS" }, { path: "/albums", name: "ALBUMS" }, { path: "/about", name: "ABOUT" }]
    }
  }
}
</script>

<template>
  <nav id="nav-main" class="wrapper-navigation">
    <ol>
      <li v-for="address in addresses">
        <RouterLink :to="{ path: address.path }">{{ address.name }}</RouterLink>
      </li>
    </ol>
  </nav>
</template>