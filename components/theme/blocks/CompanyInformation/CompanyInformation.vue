<template>
  <section class="container px15">
    <div>
      <header class="col-md-12">
        <h2 class="align-center cl-accent">{{ $t('Some helpful information.') }}</h2>
      </header>
    </div>
    <div class="row center-xs">
      <div class="split">
        <ul class="side">
          <li>fejifoje</li>
          <li>lefjfheoifj</li>
        </ul>
        <ul>
          <li>fejifoje</li>
          <li>lefjfheoifj</li>
        </ul>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'CompanyInformation'
}
</script>

<style lang="scss" scoped>
.split {
  display: flex;
  margin-top: -30%;
  background: #ffffff;
}
.side {
  width: 50%;
}
</style>
