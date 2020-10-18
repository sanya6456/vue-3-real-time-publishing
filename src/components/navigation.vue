<template>
  <nav class="navbar navbar-expand-md bg-dark navbar-dark sticky-top px-3">
      <a class="navbar-brand">Facebook</a>
      <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#responsive-nav">
          <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse text-center" id="responsive-nav">
          <ul class="navbar-nav ml-auto">
              <li class="nav-item">
                  <a href="#" class="nav-link active">Home</a>
              </li>
              <li class="nav-item">
                  <a href="#" class="nav-link">Groups</a>
              </li>
              <li class="nav-item">
                  <a href="#" class="nav-link">Chat</a>
              </li>
              <li class="nav-item">
                  <a href="#" class="nav-link">Profile</a>
              </li>
          </ul>
      </div>
  </nav>
</template>

<script>
export default {
    name: 'Navigation'
}
</script>

<style>

</style>