<template>
  <footer class="footer mt-auto py-3">
    <div class="footer-copyright text-center py-3">
      <span>© {{ date }} Copyright: </span>
      <a href="https://github.com/eraduz" target="_blank">Reda</a>
    </div>
  </footer>
</template>
<script>
export default {
  data () {
    return {
      date: new Date().getFullYear()
    }
  }
}
</script>
